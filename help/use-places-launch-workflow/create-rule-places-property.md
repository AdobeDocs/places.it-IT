---
title: Creazione di una regola per la proprietà Places Service
description: Il SDK Places tiene traccia della posizione corrente, monitora i POI configurati intorno alla posizione corrente e tiene traccia degli eventi di entrata e uscita per questi POI.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
TQID: https://experienceleague.adobe.com/jyGVmk-oKX6-5vxZBx6Mz-QF8SBYxAWssvAxJ0QLYWQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 939
ht-degree: 12%

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

* **Inserisci il POI**, che viene attivato da Places SDK quando il cliente accede al POI configurato.
* **Esci da POI**, che viene attivato da Places SDK quando il cliente esce dal POI configurato.

### Condizioni di Places Service

Le condizioni definiscono i criteri che i dati associati all’evento, o lo stato condiviso di un’estensione in tale istanza, devono soddisfare per l’azione da intraprendere. Ad esempio, puoi impostare una condizione per attivare un&#39;azione su un ingresso a un coffee shop solo nella città di San Francisco.

Il SDK Places mantiene i seguenti stati:

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
>Con questo esempio si presuppone che sia stata creata una libreria POI di tutti i coffee shop degli Stati Uniti. Per ulteriori informazioni sulla creazione di punti di interesse e librerie, vedi [Creare un punto di interesse](/help/poi-mgmt-ui/create-a-poi-ui.md) e *Creare una libreria* in [Gestire più librerie](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=it).

La procedura seguente illustra come creare una regola che invia un post a Slack quando si entra in un coffee shop a San Francisco.

L’evento, la condizione e l’azione sono definiti nei seguenti modi:

* **Evento**: evento di immissione luoghi.
* **Condizione**: la città per il **POI attuale** è San Francisco
* **Azione**: invia un postback a Slack con il nome del coffee shop immesso dal cliente.

### Prerequisito

Prima di creare una regola, devi creare un elemento dati in Adobe Experience Platform Launch. Gli elementi dati compilano automaticamente le informazioni necessarie sui punti di interesse nel messaggio di postback.

Per creare un elemento dati in Experience Platform Launch:

1. Fare clic sulla scheda **Elementi dati**.
1. Fare clic su **Aggiungi elemento dati**.
1. Digitare un nome, ad esempio **Nome attuale del coffee shop**.
1. Nell&#39;elenco a discesa **Estensione**, selezionare **Posizioni - Beta**.
1. In **Elemento dati**, seleziona **Città**.
1. Nel riquadro di destra, seleziona **Current POI**.
1. Fai clic su **Salva**.

### Creare una regola in Experience Platform Launch per Places Service

![creazione di una regola](/help/assets/placesrule.png)

1. In Experience Platform Launch, fai clic sulla scheda **[!UICONTROL Regole]**.
1. Fai clic su **[!UICONTROL Aggiungi regola]**.
1. Digitare un nome per la regola, ad esempio **[!UICONTROL Traccia voce per coffee shop in SF]**.

### Creare un evento

1. Nella sezione Eventi fare clic su **[!UICONTROL + Aggiungi]**. Gli eventi determinano quando attivare la regola.
1. Nell&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Posizioni - Beta]**.
1. Nell’elenco a discesa **[!UICONTROL Tipo di evento]**, seleziona **[!UICONTROL Enter POI]** (Inserisci POI).
1. In **[!UICONTROL Nome]**, inserisci un nome per l’evento, ad esempio **[!UICONTROL Entrare in un coffee shop]**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Crea una condizione

1. Nella sezione Condizioni fare clic su **[!UICONTROL +Aggiungi]**. Le condizioni determinano i criteri da soddisfare per l’azione da intraprendere.
1. In **[!UICONTROL Logic Type]** (Tipo di logica), seleziona Regular (Normale), che consente l’esecuzione delle azioni se la condizione viene soddisfatta.
1. Nell&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Posizioni - Beta]**.
1. In **[!UICONTROL Condition Type]** (Tipo di condizione), seleziona **[!UICONTROL Città]**.
1. Digitare il nome di una condizione, ad esempio **[!UICONTROL Coffee shop in SF]**.
1. Nel riquadro a destra, fai clic su **[!UICONTROL Current POI]**(POI attuale), quindi seleziona **[!UICONTROL San Francisco]** come una delle città dell’utente.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Crea un&#39;azione

1. Nella sezione **[!UICONTROL Azioni]**, fare clic su **[!UICONTROL + Aggiungi]**.
1. Nell&#39;elenco a discesa **[!UICONTROL Estensione]**, lascia selezionata l&#39;opzione predefinita **[!UICONTROL Core mobile]**.
1. Seleziona un tipo di azione, ad esempio **[!UICONTROL Invia postback]**.

   a. In **[!UICONTROL URL]** digitare l&#39;URL di postback per Slack, ad esempio `https://hooks.slack.com/services/`.

   b. Per inviare un corpo del post, selezionare la casella di controllo **[!UICONTROL Aggiungi corpo del post]**.

   c. In **[!UICONTROL Corpo post]**, aggiungi il corpo del post, ad esempio: `{ "text": "A customer has entered" }`

   c. Digita un tipo di contenuto, ad esempio **[!UICONTROL application/json]**.

   d. Selezionare un valore di timeout, ad esempio **[!UICONTROL 5]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

### Pubblicare la regola

1. Per attivare la regola, devi pubblicarla. Per ulteriori informazioni sulla pubblicazione della regola in Experience Platform Launch, vedi [Pubblicazione](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=it).

### Oltre le entrate e le uscite

L’utilizzo delle entrate e delle uscite del recinto geografico di Places Service per attivare le regole in Experience Platform Launch è incredibilmente efficace, ma puoi anche utilizzare i dati sulla posizione come condizione affinché altri eventi vengano attivati. Ad esempio, puoi avere un trigger di evento Track Action core mobile pronto per essere attivato in base a un particolare evento di chiamata trackAction all&#39;interno dell&#39;app. In base a questo evento, puoi inserire ulteriori condizioni di posizione nell’evento prima che venga eseguita un’azione. Ad esempio, apri un sondaggio in-app quando si verifica un evento di acquisto `trackAction`, ma **solo** se la posizione corrente dell&#39;utente include metadati specifici di Places Service.

![crea una condizione](/help/assets/places-condition.png)
