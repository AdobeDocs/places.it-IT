---
title: Creazione di una regola per la proprietà Places Service
description: 'L’SDK Luoghi tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per tali POI. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# Creare regole di entrata e uscita {#create-entry-exit-rules}

Con le estensioni Places e Places Monitor installate nell’applicazione mobile, puoi creare regole in Adobe Experience Platform Launch che vengono attivate o condizionate per i dati della posizione, inclusi gli eventi di ingresso e uscita dalla posizione.

## Regole

È possibile configurare una regola, composta da un evento, una condizione e un&#39;azione. Ogni regola è composta dai seguenti elementi:

* Uno o più eventi
* (Facoltativo) condizioni
* Una o più azioni

### Eventi di servizio Luoghi

Il servizio Luoghi offre i seguenti eventi in cui è possibile eseguire una regola:

* **Inserisci un POI**, attivato dall’SDK di Places quando il cliente accede al POI configurato dall’utente.
* **Esci dal POI**, attivato dall’SDK di Places quando il cliente esce dal POI configurato.

### Posizioni Condizioni di servizio

Le condizioni definiscono i criteri che i dati associati all&#39;evento, o lo stato condiviso di un&#39;estensione in tale istanza, devono soddisfare affinché l&#39;azione venga eseguita. Ad esempio, è possibile impostare una condizione per attivare un&#39;azione su una voce di un coffee shop solo nella città di San Francisco.

L’SDK Luoghi mantiene gli stati seguenti:

* POI correnti, che si riferisce al POI in cui il cliente si trova attualmente.
* Ultimo POI uscito, che si riferisce al POI più recente che il cliente è uscito.
* Ultimo POI inserito, che fa riferimento al POI più recente immesso dal cliente.

Ciascun POI contiene i seguenti elementi di dati:

* ID
* Nome
* Latitudine/longitudine
* Raggio
* Metadati quali città, paese, stato, categoria

### Azioni

Le azioni definiscono le operazioni che l&#39;app eseguirà in risposta alla condizione per cui la regola è soddisfatta per l&#39;evento generato. Ad esempio, quando il cliente accede al POI, puoi configurare un messaggio di benvenuto da visualizzare sul dispositivo mobile.

## Create una regola: un esempio

>[!CAUTION]
>
>Con questo esempio si presuppone che sia stata creata una libreria POI di tutti i coffee shop degli Stati Uniti. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

La procedura seguente è un esempio di come creare una regola che invia un post a Slack quando si entra in un coffee shop a San Francisco.

L’evento, la condizione e l’azione sono definiti nei seguenti modi:

* **Evento**: Posiziona l&#39;evento di immissione.
* **Condizione**: la città per il **POI attuale** è San Francisco
* **Azione**: Invia un postback a Slack il nome del coffee shop immesso dal cliente.

### Prerequisito

Prima di creare una regola, è necessario creare un elemento dati in Adobe Experience Platform Launch. Gli elementi dati popolano automaticamente le informazioni necessarie sul POI nel messaggio di postback.

Per creare un elemento dati in Experience Platform Launch:

1. Fare clic sulla scheda **Elementi** dati.
1. Fare clic su **Aggiungi elemento** dati.
1. Digitare un nome, ad esempio **Nome** caffetteria corrente.
1. Nell’elenco a discesa **Estensione** , selezionate **Luoghi - Beta**.
1. In **Elemento dati**, seleziona **Città**.
1. Nel riquadro a destra, selezionare **POI** correnti.
1. Fai clic su **Salva**.

### Creare una regola in Experience Platform Launch for Places Service

![creazione di una regola](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]**tab.
1. Fai clic su **[!UICONTROL Add Rule]**.
1. Digitare un nome per la regola, ad esempio **[!UICONTROL Track entry for coffee shop in SF]**.

### Crea un evento

1. Nella sezione Eventi, fate clic su **[!UICONTROL + Add]**. Gli eventi determinano quando attivare la regola.
1. Nell&#39;elenco a **[!UICONTROL Extension]**discesa, selezionare**[!UICONTROL Places – Beta]**.
1. Nell&#39;elenco a **[!UICONTROL Event Type]**discesa, selezionare**[!UICONTROL Enter POI]**.
1. In **[!UICONTROL Name]**, immettete un nome per l’evento, ad esempio**[!UICONTROL Entering a coffee shop]**.
1. Fai clic su **[!UICONTROL Keep Changes]**.

### Crea una condizione

1. Nella sezione Condizioni, fate clic su **[!UICONTROL +Add]**. Le condizioni determinano quali criteri devono essere soddisfatti per l&#39;azione da intraprendere.
1. In **[!UICONTROL Logic Type]**(Tipo di logica), seleziona Regular (Normale), che consente l’esecuzione delle azioni se la condizione viene soddisfatta.
1. Nell&#39;elenco a **[!UICONTROL Extension]**discesa, selezionare**[!UICONTROL Places – Beta]**.
1. In **[!UICONTROL Condition Type]**, selezionate**[!UICONTROL City]**.
1. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select**[!UICONTROL San Francisco]** as one of your cities.
1. Fai clic su **[!UICONTROL Keep Changes]**.

### Crea un&#39;azione

1. In the **[!UICONTROL Actions]**section, click**[!UICONTROL + Add]**.
1. Nell&#39;elenco a **[!UICONTROL Extension]**discesa, lasciare selezionata l&#39;**[!UICONTROL Mobile Core]** opzione predefinita.
1. Selezionare un tipo di azione, ad esempio **[!UICONTROL Send Postback]**.

   a. In **[!UICONTROL URL]**, digitate l’URL postback per Slack, ad esempio`https://hooks.slack.com/services/`.

   b. Per inviare un corpo del post, selezionate la **[!UICONTROL Add Post Body]**casella di controllo.

   c. In **[!UICONTROL Post Body]**, aggiungete il corpo del post, ad esempio:`{ "text": "A customer has entered" }`

   c. Digitate un tipo di contenuto, ad esempio **[!UICONTROL application/json]**.

   d. Selezionate un valore di timeout, ad esempio **[!UICONTROL 5]**.

1. Fai clic su **[!UICONTROL Keep Changes]**.

### Pubblicare la regola

1. Per attivare la regola, è necessario pubblicarla. Per ulteriori informazioni sulla pubblicazione della regola in Experience Platform Launch, consulta [Pubblicazione](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Pensare oltre le entrate e le uscite

L&#39;utilizzo di voci ed uscite del servizio Places per attivare le regole in Experience Platform Launch è incredibilmente potente, ma puoi anche utilizzare i dati della posizione come condizione per attivare altri eventi. Ad esempio, potresti avere un attivatore di eventi di tracciamento core Mobile pronto per essere attivato in base a un particolare evento di chiamata trackAction all’interno dell’app. In base a questo evento, potete inserire condizioni di posizione aggiuntive per l&#39;evento prima che venga eseguita un&#39;azione. Ad esempio, aprite un sondaggio in-app quando si verifica un `trackAction` evento di acquisto, ma **solo** se la posizione corrente dell&#39;utente include metadati specifici del servizio Luoghi.

![creare una condizione](/help/assets/places-condition.png)