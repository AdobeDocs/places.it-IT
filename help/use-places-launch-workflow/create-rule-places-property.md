---
title: Creazione di una regola per la proprietà Places Service
description: L’SDK Places tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per questi POI.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 13%

---

# Creare regole di entrata e di uscita {#create-entry-exit-rules}

Con l’estensione Luoghi e una soluzione di monitoraggio dell’area installata nell’app mobile, puoi creare regole in Adobe Experience Platform Launch che vengono attivate o condizionate per i dati della posizione, inclusi gli eventi di entrata e uscita dalla posizione.

## Regole

Puoi configurare una regola, composta da un evento, una condizione e un’azione. Ogni regola è composta dalle seguenti:

* Uno o più eventi
* Condizioni (facoltative)
* Una o più azioni

### Eventi Places Service

Places Service offre i seguenti eventi sui quali è possibile eseguire una regola:

* **Inserisci POI**, attivato dall’SDK Places quando il cliente accede al POI configurato.
* **Esci da POI**, attivato dall’SDK Places quando il cliente esce dal POI configurato.

### Condizioni di Places Service

Le condizioni definiscono i criteri che i dati associati all’evento, o lo stato condiviso di un’estensione in tale istanza, devono soddisfare per l’azione da intraprendere. Ad esempio, puoi impostare una condizione per attivare un&#39;azione su un ingresso a un coffee shop solo nella città di San Francisco.

L’SDK Luoghi mantiene i seguenti stati:

* POI corrente, che si riferisce al POI in cui il cliente si trova attualmente.
* Last exited POI (Ultimo punto di interesse in uscita), che si riferisce al punto di interesse più recente chiuso dal cliente.
* Ultimo POI inserito, che si riferisce al POI più recente inserito dal cliente.

Ogni POI contiene i seguenti elementi di dati:

* ID
* Nome
* Latitudine/longitudine
* Raggio
* Metadati come città, paese, stato, categoria

### Azioni

Le azioni definiscono ciò che l&#39;app farà in risposta alla condizione per cui la regola viene soddisfatta per l&#39;evento attivato. Ad esempio, quando il cliente accede al punto di interesse, puoi configurare un messaggio di benvenuto da visualizzare sul suo dispositivo mobile.

## Creare una regola: un esempio

>[!CAUTION]
>
>Con questo esempio si presuppone che sia stata creata una libreria POI di tutti i coffee shop degli Stati Uniti. Per ulteriori informazioni sulla creazione di POI e librerie, consulta [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) e *Creare una libreria* in [Gestire più librerie](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

La procedura seguente illustra come creare una regola che invia un post allo Slack quando si entra in un coffee shop a San Francisco.

L’evento, la condizione e l’azione sono definiti nei seguenti modi:

* **Evento**: evento di immissione Luoghi.
* **Condizione**: la città per il **POI attuale** è San Francisco
* **Azione**: invia un postback per lo Slack del nome del coffee shop che è stato immesso dal cliente.

### Prerequisito

Prima di creare una regola, devi creare un elemento dati in Adobe Experience Platform Launch. Gli elementi dati compilano automaticamente le informazioni necessarie sui punti di interesse nel messaggio di postback.

Per creare un elemento dati nel Experience Platform Launch:

1. Fai clic su **Elementi dati** scheda.
1. Fai clic su **Aggiungi elemento dati**.
1. Digita un nome, ad esempio: **Nome attuale del coffee shop**.
1. In **Estensione** elenco a discesa, seleziona **Places - Beta**.
1. In **Elemento dati**, seleziona **Città**.
1. Nel riquadro di destra, seleziona **POI corrente**.
1. Fai clic su **Salva**.

### Creazione di una regola nel Experience Platform Launch per Places Service

![creazione di una regola](/help/assets/placesrule.png)

1. In Experience Platform Launch, fai clic sulla scheda **[!UICONTROL Regole]**.
1. Fai clic su **[!UICONTROL Aggiungi regola]**.
1. Digita un nome per la regola, ad esempio: **[!UICONTROL Tracciamento di ingresso per coffee shop in SF]**.

### Crea un evento

1. Nella sezione Eventi, fai clic su **[!UICONTROL + Aggiungi]**. Gli eventi determinano quando attivare la regola.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places - Beta]**.
1. Nell’elenco a discesa **[!UICONTROL Tipo di evento]**, seleziona **[!UICONTROL Enter POI]** (Inserisci POI).
1. In **[!UICONTROL Nome]**, inserisci un nome per l’evento, ad esempio **[!UICONTROL Entrare in un coffee shop]**.
1. Clic **[!UICONTROL Mantieni modifiche]**.

### Crea una condizione

1. Nella sezione Condizioni fare clic su **[!UICONTROL +Aggiungi]**. Le condizioni determinano i criteri da soddisfare per l’azione da intraprendere.
1. In **[!UICONTROL Logic Type]** (Tipo di logica), seleziona Regular (Normale), che consente l’esecuzione delle azioni se la condizione viene soddisfatta.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places - Beta]**.
1. In **[!UICONTROL Condition Type]** (Tipo di condizione), seleziona **[!UICONTROL Città]**.
1. Digita un nome di condizione, ad esempio: **[!UICONTROL Caffetteria in SF]**.
1. Nel riquadro a destra, fai clic su **[!UICONTROL Current POI]**(POI attuale), quindi seleziona **[!UICONTROL San Francisco]** come una delle città dell’utente.
1. Clic **[!UICONTROL Mantieni modifiche]**.

### Crea un&#39;azione

1. In **[!UICONTROL Azioni]** , fare clic su **[!UICONTROL + Aggiungi]**.
1. In **[!UICONTROL Estensione]** nell&#39;elenco a discesa, lasciare il valore predefinito **[!UICONTROL Core mobile]** opzione selezionata.
1. Seleziona un tipo di azione, ad esempio: **[!UICONTROL Invia postback]**.

   a. In entrata **[!UICONTROL URL]**, digita l’URL del postback per lo Slack, ad esempio, `https://hooks.slack.com/services/`.

   b. Per inviare un corpo del post, selezionare **[!UICONTROL Aggiungi corpo del post]** casella di controllo.

   c. In entrata **[!UICONTROL Corpo del post]**, aggiungi il corpo del post, ad esempio: `{ "text": "A customer has entered" }`

   c. Digita un tipo di contenuto, ad esempio **[!UICONTROL application/json]**.

   d. Seleziona un valore di timeout, ad esempio: **[!UICONTROL 5]**.

1. Clic **[!UICONTROL Mantieni modifiche]**.

### Pubblicare la regola

1. Per attivare la regola, devi pubblicarla. Per ulteriori informazioni sulla pubblicazione della regola nel Experience Platform Launch, vedi [Pubblicazione](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Oltre le entrate e le uscite

L’utilizzo delle entrate e delle uscite del recinto geografico di Places Service per attivare le regole nel Experience Platform Launch è incredibilmente efficace, ma puoi anche utilizzare i dati sulla posizione come condizione affinché altri eventi vengano attivati. Ad esempio, puoi avere un trigger di evento Track Action core mobile pronto per essere attivato in base a un particolare evento di chiamata trackAction all&#39;interno dell&#39;app. In base a questo evento, puoi inserire ulteriori condizioni di posizione nell’evento prima che venga eseguita un’azione. Ad esempio, apri un sondaggio in-app quando un acquisto `trackAction` si verifica, ma **solo** se la posizione corrente dell’utente include metadati specifici di Places Service.

![creare una condizione](/help/assets/places-condition.png)
