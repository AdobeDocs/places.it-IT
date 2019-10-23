---
title: Creazione di una regola per la proprietà Luoghi
seo-title: Creazione di una regola per la proprietà Luoghi
description: 'L’SDK Luoghi tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per tali POI. '
seo-description: 'L’SDK Luoghi tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per tali POI. '
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Creare una regola per la proprietà Luoghi {#creating-rule-places-property}

L’SDK del servizio di localizzazione tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per tali POI.

## Regole

È possibile configurare una regola, composta da un evento, una condizione e un'azione. Ogni regola è composta dai seguenti elementi:

* Uno o più eventi
* (Facoltativo) condizioni
* Una o più azioni

### Eventi

Luoghi offre i seguenti eventi in cui è possibile eseguire una regola:

* **[!UICONTROL Enter POI]**, attivato dall’SDK Places quando il cliente accede al POI configurato dall’utente.
* **[!UICONTROL Exit POI]**, attivato dall’SDK Places quando il cliente esce dall’POI configurato dall’utente.

### Condizioni

Le condizioni definiscono i criteri che i dati associati all'evento, o lo stato condiviso di un'estensione in tale istanza, devono soddisfare affinché l'azione venga eseguita. Ad esempio, è possibile impostare una condizione per attivare un'azione su una voce di un coffee shop solo nella città di San Francisco.

L’SDK del servizio di localizzazione mantiene gli stati seguenti:

* POI correnti, che si riferisce al POI in cui il cliente si trova attualmente.
* Ultimo POI uscito, che si riferisce al POI più recente che il cliente è uscito.
* Ultimo POI inserito, che fa riferimento al POI più recente immesso dal cliente.

Ciascun POI contiene i seguenti elementi di dati:

* ID
* Nome:
* Latitudine/longitudine
* Raggio
* Metadati quali città, paese, stato, categoria

### Azioni

Le azioni definiscono le operazioni che l'app eseguirà in risposta alla condizione per cui la regola è soddisfatta per l'evento generato. Ad esempio, quando il cliente accede al POI, puoi configurare un messaggio di benvenuto da visualizzare sul dispositivo mobile.

## Create una regola: un esempio

>[!CAUTION]
>
>Questo esempio presuppone che sia stata creata una libreria POI di tutti i coffee shop degli Stati Uniti. Per ulteriori informazioni sulla creazione di POI e librerie, consultate [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) e *Creare una libreria* in [Gestione librerie nell’interfaccia](/help/poi-mgmt-ui/manage-libraries-in-the-places-ui.md)Luoghi.

La procedura seguente è un esempio di come creare una regola che invia un post a Slack quando si entra in un coffee shop a San Francisco.

L’evento, la condizione e l’azione sono definiti nei seguenti modi:

* **Evento**: Evento voce Servizio posizione.
* **Condizione**: Città per il POI **attuale** è San Francisco
* **Azione**: Invia un postback a Slack il nome del coffee shop immesso dal cliente.

### Prerequisito

Prima di creare una regola, è necessario creare un elemento dati in Experience Platform Launch. Gli elementi dati popolano automaticamente le informazioni necessarie sul POI nel messaggio di postback.

Per creare un elemento dati in Experience Platform Launch:

1. Click the **[!UICONTROL Data Elements]** tab.
2. Fai clic su **[!UICONTROL Add Data Element]**.
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. Nell'elenco a **[!UICONTROL Extension]** discesa, selezionare **[!UICONTROL Places – Beta]**.
5. In **[!UICONTROL Data Element]**, selezionate **[!UICONTROL City]**.
6. Nel riquadro a destra, selezionare **POI** correnti.
7. Fai clic su **[!UICONTROL Save]**.

### Creare una regola in Experience Platform Launch for Location Service

![](//help/assets/create-a-rule.png)

1. In Experience Platform Launch, fai clic sulla **[!UICONTROL Rules]** scheda.
2. Click **Add Rule**.
3. Digitare un nome per la regola, ad esempio, **Track entry for coffee shop in SF**.

### Crea un evento

1. Nella sezione Eventi, fate clic su **[!UICONTROL + Add]**. Gli eventi determinano quando attivare la regola.
2. Nell'elenco a **[!UICONTROL Extension]** discesa, selezionare **[!UICONTROL Places – Beta]**.
3. Nell'elenco a **[!UICONTROL Event Type]** discesa, selezionare **[!UICONTROL Enter POI]**.
4. In **[!UICONTROL Name]**, immettete un nome per l’evento, ad esempio **[!UICONTROL Entering a coffee shop]**.
5. Fai clic su **[!UICONTROL Keep Changes]**.

### Crea una condizione

1. Nella sezione Condizioni, fate clic su **[!UICONTROL +Add]**. Le condizioni determinano quali criteri devono essere soddisfatti per l'azione da intraprendere.
2. In **[!UICONTROL Logic Type]**, selezionate Regolare, che consente l'esecuzione di azioni se la condizione è soddisfatta.
3. Nell’elenco a discesa **Estensione** , selezionate **[!UICONTROL Places – Beta]**.
4. In **[!UICONTROL Condition Type]**, selezionate **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. Nel riquadro a destra, fare clic su **[!UICONTROL Current POI]** e, nell’elenco a discesa, selezionare **[!UICONTROL San Francisco]** una delle città.
7. Fai clic su **[!UICONTROL Keep Changes]**.

### Crea un'azione

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTRO+ Aggiungi]**.
2. Nell’elenco a discesa **[!UICONTRO Estensione]** , lasciate selezionata l’opzione **[!UICONTRO Mobile Core]** predefinita.
3. Selezionare un tipo di azione, ad esempio **[!UICONTRO Invia postback]**.

   a. In **[!UICONTROL URL]**, digitate l’URL postback per Slack, ad esempio `https://hooks.slack.com/services/`.

   b. Per inviare un corpo del post, seleziona la casella di controllo **[!UICONTRO Aggiungi corpo]** del post.

   c. In Corpo **[!UICONTRO ]** post, aggiungete il corpo del post, ad esempio: `{ "text": "A customer has entered" }`

   c. Digitate un tipo di contenuto, ad esempio **[!UICONTRO application/json]**.

   d. Selezionate un valore di timeout, ad esempio **5**.

4. Click **[!UICONTRO Keep Changes]**.

### Pubblicare la regola

1. Per attivare la regola, è necessario pubblicarla. Per ulteriori informazioni sulla pubblicazione della regola in Experience Platform Launch, consulta [Pubblicazione](https://docs.adobelaunch.com/launch-reference/publishing).