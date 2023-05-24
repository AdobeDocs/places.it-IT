---
title: Notifiche push con Places Service
description: Questa sezione fornisce informazioni sull’utilizzo di Places Service con le notifiche push in Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 3%

---

# Notifiche push con Places Service {#push-notifications}

In questa sezione imparerai a utilizzare informazioni storiche sulla geolocalizzazione per eseguire il targeting delle notifiche push distribuite tramite Adobe Campaign Standard.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un’app mobile configurata con Adobe Experience Platform Mobile SDK, incluso [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrare [SDK di Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nell’app.
* Aggiungi il [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione dell’app mobile.

* [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI di Places Service.

* Abilitare e installare [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creazione di elementi dati nel Experience Platform Launch

Dopo aver verificato che l’estensione Luoghi e una soluzione di monitoraggio dell’area ([Documentazione di CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS, oppure [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) funzionano correttamente nell&#39;applicazione, è necessario creare elementi dati nel Experience Platform Launch. Gli elementi dati ti consentono di leggere le informazioni fornite dalle estensioni che arrivano attraverso l’hub eventi dell’SDK di Mobile e fungono da alias per recuperare i dati dall’applicazione client. Per recuperare i dati dalle estensioni di Places e inviare le informazioni di Places Service a Campaign, devi creare alcuni elementi di dati.

Per creare un elemento dati:

1. Nella proprietà mobile del Experience Platform Launch, fai clic su **[!UICONTROL Elementi dati]** e fai clic su **[!UICONTROL Aggiungi elemento dati]**.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places Service]**.
1. Dalla sezione **[!UICONTROL Tipo di elemento dati]** elenco a discesa, seleziona **[!UICONTROL Nome]**.
1. Nel riquadro a destra è possibile selezionare **[!UICONTROL POI corrente]** che recupera il nome del POI in cui si trova l’utente.

   **[!UICONTROL Ultimo inserimento]** recupera il nome dell’ultimo POI immesso dall’utente e **[!UICONTROL Ultima uscita]** fornisce il nome dell’ultimo punto di interesse lasciato dall’utente. In questo esempio abbiamo selezionato **[!UICONTROL Ultimo inserimento]** e ha digitato un nome per l’elemento dati, ad esempio **[!UICONTROL Nome ultimo punto di interesse immesso]** e su cui è stato fatto clic **[!UICONTROL Salva]**.

   ![&quot;Messaggi push in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Ripeti i passaggi da 1 a 4 precedenti e crea elementi dati per *Latitudine ultimo POI inserito*, *Longitudine ultimo POI inserito*, e *Raggio ultimo POI inserito*.

Oltre agli elementi dati per Places Service, assicurati di creare elementi dati core per dispositivi mobili per *ID app* e *ID EXPERIENCE CLOUD*.

## Creare una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole di Experience Platform Launch consentono di creare flussi di lavoro complessi e con più soluzioni basati su attivatori di eventi. Con le regole, puoi creare nuove regole o modificare quelle esistenti e distribuire dinamicamente gli aggiornamenti nelle app mobili. Nell’esempio seguente, la regola viene attivata quando un utente accede a un POI delimitato da geotargeting. Dopo l’attivazione della regola, viene inviato un aggiornamento a Campaign Standard per registrare una voce in un POI specifico per un particolare utente in base all’ID Experience Cloud.

1. Nella proprietà mobile del Experience Platform Launch, nella **[!UICONTROL Regole]** , fare clic su **[!UICONTROL Aggiungi regola]**.
1. Sotto **[!UICONTROL Eventi]** , fare clic su **[!UICONTROL +]** e seleziona **[!UICONTROL Places Service]** come estensione.
1. Per **[!UICONTROL Tipo di evento]**, seleziona **[!UICONTROL Inserisci POI]**.
1. Denomina la regola, ad esempio: **POI immesso dall’utente**.
1. Clic **[!UICONTROL Mantieni modifiche]**.
1. Lascia **[!UICONTROL Condizioni]** sezione vuota.

   Questa sezione ti consente di filtrare o porre restrizioni su quando attivare questa regola.

1. Sotto **[!UICONTROL Azioni]** , fare clic su **[!UICONTROL +]**.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Core mobile]** e nella **[!UICONTROL Tipo di azione]** elenco a discesa, seleziona **[!UICONTROL Invia postback]**.
1. In entrata **[!UICONTROL URL]**, devi costruire l’endpoint delle posizioni Campaign Standard.

   L’URL deve avere un aspetto simile a `https:///rest/head/mobileAppV5//locations/`.
Assicurati di utilizzare gli elementi dati corretti creati in precedenza per il server Campaign e la pKey.

1. Fai clic sulla casella per aggiungere un corpo del post e inviare quanto segue:

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. Assicurati di utilizzare gli elementi dati creati nella sezione precedente.
1. In **[!UICONTROL Tipo di contenuto]**, digita **[!UICONTROL application/json]**.
1. Clic **[!UICONTROL Mantieni modifiche]**.

>[!IMPORTANT]
>
>* Potrebbe essere utile impostare un hook web di Slack come azione aggiuntiva per convalidare l’attivazione delle voci e la raccolta dei dati corretti.
>* Ricorda di pubblicare le modifiche recenti nell&#39;app per assicurarti che la regola e tutti gli elementi dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, avvia di nuovo l’app mobile per ottenere gli aggiornamenti di configurazione più recenti.


## Utilizzare i dati sulla posizione per eseguire il targeting dei messaggi di Campaign

Ora che i dati sulla posizione sono compilati in Campaign, possiamo utilizzare i POI come strumento per segmenti di pubblico.

1. Nell’istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Creare una notifica push]**.
1. Per il tipo di notifica push, seleziona **[!UICONTROL Inviare messaggi push ai profili di Campaign]**.
1. Clic **[!UICONTROL Successivo]** e digita i dettagli generali.
1. Nella schermata Pubblico, fai clic su **[!UICONTROL Conteggio]** per determinare a quanti utenti stimati verrà inviata la notifica push.

   >[!TIP]
   >
   >In questo esempio, il conteggio sarà 3, perché sono presenti tre dispositivi installati su cui viene testata l’applicazione.

1. Nel riquadro a sinistra, espandere **[!UICONTROL Profilo]** e trascinare il **[!UICONTROL Posizione POI]** filtrare fino all&#39;area principale.
1. Nella finestra del filtro POI, inserisci il nome esatto del POI di cui desideri eseguire il targeting.

   >[!TIP]
   >
   >Puoi effettuare selezioni aggiuntive per determinare il periodo di tempo trascorso dalla precedente visita dell’utente a questo POI.

   ![&quot;Messaggi push 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Fai clic su **[!UICONTROL Conferma]**.
1. Esegui di nuovo il conteggio nella parte superiore per vedere come cambia la dimensione del pubblico.

   Se non vedi l&#39;aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessun dispositivo ha attivato una voce. In questa situazione diventa utile disporre del web hook di Slack, perché puoi visualizzare un elenco di voci POI da vari dispositivi di test.

1. Puoi trascinare altri filtri di posizione POI per includere più POI nel messaggio.
1. Fai clic su **[!UICONTROL Avanti]** per completare la creazione della notifica push per la consegna.

   ![&quot;Messaggi push 3 in ACS&quot;](/help/assets/ACS_push3.png)

L’utilizzo di Places Service con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base alle entrate e alle uscite del recinto geografico. Questa integrazione ti aiuta a creare casi d’uso più personalizzati e contestuali.
