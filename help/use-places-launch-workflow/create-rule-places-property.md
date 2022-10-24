---
title: Creazione di una regola per la proprietà Places Service
description: L’SDK di Places tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per questi POI.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 13%

---

# Creare regole di entrata e di uscita {#create-entry-exit-rules}

Con l’estensione Places e una soluzione di monitoraggio regionale installata nella tua app mobile, puoi creare regole in Adobe Experience Platform Launch che vengono attivate o condizionate per i dati sulla posizione, inclusi gli eventi di ingresso e uscita dalla posizione.

## Regole

Puoi configurare una regola, composta da un evento, una condizione e un&#39;azione. Ogni regola è composta dai seguenti elementi:

* Uno o più eventi
* (Facoltativo) condizioni
* Una o più azioni

### Eventi di Places Service

Places Service offre i seguenti eventi in cui è possibile eseguire una regola:

* **Inserisci POI**, che viene attivata dall’SDK di Places quando il cliente accede al POI configurato.
* **Esci dal POI**, che viene attivata dall’SDK di Places quando il cliente esce dal POI configurato.

### Luoghi Condizioni di servizio

Le condizioni definiscono i criteri che i dati associati all’evento, o lo stato condiviso di un’estensione in tale istanza, devono soddisfare per l’azione da eseguire. Ad esempio, puoi impostare una condizione per attivare un’azione su una voce di un coffee shop solo nella città di San Francisco.

L’SDK di Places mantiene i seguenti stati:

* POI attuale, che si riferisce al POI in cui il cliente si trova attualmente.
* Ultimo POI uscito, che si riferisce al POI più recente uscito dal tuo cliente.
* Ultimo POI inserito, che si riferisce al POI più recente inserito dal tuo cliente.

Ogni POI contiene i seguenti elementi dati:

* ID
* Nome
* Latitudine/longitudine
* Raggio
* Metadati quali città, paese, stato, categoria

### Azioni

Le azioni definiscono le operazioni che l’app eseguirà in risposta alla condizione per cui la regola viene soddisfatta per l’evento attivato. Ad esempio, quando il cliente accede al tuo POI, puoi configurare un messaggio di benvenuto da visualizzare sul suo dispositivo mobile.

## Crea una regola: un esempio

>[!CAUTION]
>
>Con questo esempio si presuppone che sia stata creata una libreria POI di tutti i coffee shop degli Stati Uniti. Per ulteriori informazioni sulla creazione di POI e librerie, vedi [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) e *Creare una libreria* in [Gestire più librerie](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

La procedura seguente è un esempio di come creare una regola che restituisce un post allo Slack quando si entra in un coffee shop a San Francisco.

L’evento, la condizione e l’azione vengono definiti nei seguenti modi:

* **Evento**: Evento di ingresso Luoghi.
* **Condizione**: la città per il **POI attuale** è San Francisco
* **Azione**: Invia un postback allo Slack del nome del coffee shop immesso dal cliente.

### Prerequisito

Prima di creare una regola, devi creare un elemento dati in Adobe Experience Platform Launch. Gli elementi dati compilano automaticamente le informazioni necessarie sul tuo POI nel messaggio di postback.

Per creare un elemento dati nel Experience Platform Launch:

1. Fai clic sul pulsante **Elementi dati** scheda .
1. Fai clic su **Aggiungi elemento dati**.
1. Digita un nome, ad esempio **Nome attuale del bar**.
1. In **Estensione** elenco a discesa, seleziona **Luoghi - Beta**.
1. In **Elemento dati**, seleziona **Città**.
1. Nel riquadro di destra, seleziona **POI attuale**.
1. Fai clic su **Salva**.

### Creare una regola in Experience Platform Launch per Places Service

![creazione di una regola](/help/assets/placesrule.png)

1. In Experience Platform Launch, fai clic sulla scheda **[!UICONTROL Regole]**.
1. Fai clic su **[!UICONTROL Aggiungi regola]**.
1. Digita un nome per la regola, ad esempio: **[!UICONTROL Ingresso a binario per caffetteria in SF]**.

### Crea un evento

1. Nella sezione Eventi, fai clic su **[!UICONTROL + Aggiungi]**. Gli eventi determinano quando attivare la regola.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Luoghi - Beta]**.
1. Nell’elenco a discesa **[!UICONTROL Tipo di evento]**, seleziona **[!UICONTROL Enter POI]** (Inserisci POI).
1. In **[!UICONTROL Nome]**, inserisci un nome per l’evento, ad esempio **[!UICONTROL Entrare in un coffee shop]**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Crea una condizione

1. Nella sezione Condizioni, fai clic su **[!UICONTROL +Aggiungi]**. Le condizioni determinano i criteri da soddisfare per l&#39;azione da intraprendere.
1. In **[!UICONTROL Logic Type]** (Tipo di logica), seleziona Regular (Normale), che consente l’esecuzione delle azioni se la condizione viene soddisfatta.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Luoghi - Beta]**.
1. In **[!UICONTROL Condition Type]** (Tipo di condizione), seleziona **[!UICONTROL Città]**.
1. Digita un nome per la condizione, ad esempio **[!UICONTROL Negozio di caffè in SF]**.
1. Nel riquadro a destra, fai clic su **[!UICONTROL Current POI]**(POI attuale), quindi seleziona **[!UICONTROL San Francisco]** come una delle città dell’utente.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Crea un&#39;azione

1. In **[!UICONTROL Azioni]** sezione, fai clic su **[!UICONTROL + Aggiungi]**.
1. In **[!UICONTROL Estensione]** elenco a discesa, lascia il valore predefinito **[!UICONTROL Core mobile]** opzione selezionata.
1. Seleziona un tipo di azione, ad esempio **[!UICONTROL Invia postback]**.

   a) In **[!UICONTROL URL]**, digita l’URL postback per Slack, ad esempio: `https://hooks.slack.com/services/`.

   b) Per inviare un corpo del post, seleziona la **[!UICONTROL Aggiungi corpo del post]** casella di controllo.

   c. Ingresso **[!UICONTROL Corpo del post]**, aggiungi il corpo del post, ad esempio: `{ "text": "A customer has entered" }`

   c. Digitare un tipo di contenuto, ad esempio **[!UICONTROL application/json]**.

   d. Seleziona un valore di timeout, ad esempio **[!UICONTROL 5]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Pubblicare la regola

1. Per attivare la regola, devi pubblicarla. Per ulteriori informazioni sulla pubblicazione della regola in Experience Platform Launch, vedi [Pubblicazione](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Pensare oltre le entrate e le uscite

L’utilizzo di voci ed uscite di geotargeting di Places Service per attivare le regole in Experience Platform Launch è incredibilmente potente, ma puoi anche utilizzare i dati di posizione come condizione per attivare altri eventi. Ad esempio, potresti avere un trigger di evento Track Action Mobile Core per attivarsi in base a un particolare evento di chiamata trackAction all’interno dell’app. In base a questo evento, puoi inserire condizioni di posizione aggiuntive per l’evento prima che venga eseguita un’azione. Ad esempio, apri un sondaggio in-app quando un acquisto `trackAction` si verifica un evento, ma **only** se la posizione corrente dell’utente include metadati specifici del servizio Places.

![creare una condizione](/help/assets/places-condition.png)
