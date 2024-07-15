---
title: Notifiche push con Places Service
description: Questa sezione fornisce informazioni sull’utilizzo di Places Service con le notifiche push in Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# Notifiche push con Places Service {#push-notifications}

In questa sezione imparerai a utilizzare informazioni storiche sulla geolocalizzazione per eseguire il targeting delle notifiche push distribuite tramite Adobe Campaign Standard.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un&#39;app mobile configurata con l&#39;SDK di Adobe Experience Platform Mobile, inclusa l&#39;estensione [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integra [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nella tua app.
* Aggiungi l&#39;[estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione della tua app mobile.

* [Crea un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell&#39;interfaccia di gestione POI di Places Service.

* Abilita e installa l&#39;estensione [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creazione di elementi dati nel Experience Platform Launch

Dopo aver verificato che l&#39;estensione Places e una soluzione di monitoraggio dell&#39;area ([documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS o [documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) funzionino correttamente nell&#39;applicazione, devi creare gli elementi dati nel Experience Platform Launch. Gli elementi dati ti consentono di leggere le informazioni fornite dalle estensioni che arrivano attraverso l’hub eventi dell’SDK di Mobile e fungono da alias per recuperare i dati dall’applicazione client. Per recuperare i dati dalle estensioni di Places e inviare le informazioni di Places Service a Campaign, devi creare alcuni elementi di dati.

Per creare un elemento dati:

1. Nella tua proprietà mobile di Experience Platform Launch, fai clic sulla scheda **[!UICONTROL Elementi dati]** e poi su **[!UICONTROL Aggiungi elemento dati]**.
1. Nell&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Places Service]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Tipo di elemento dati]**, selezionare **[!UICONTROL Nome]**.
1. Nel riquadro a destra è possibile selezionare **[!UICONTROL Current POI]** che recupera il nome del POI in cui si trova l&#39;utente.

   **[!UICONTROL Last Entered]** recupera il nome dell&#39;ultimo POI immesso dall&#39;utente e **[!UICONTROL Last Exited]** fornisce il nome dell&#39;ultimo POI lasciato dall&#39;utente. In questo esempio, abbiamo selezionato **[!UICONTROL Ultimo inserimento]** e digitato un nome per l&#39;elemento dati, ad esempio **[!UICONTROL Nome ultimo POI inserito]**, quindi abbiamo fatto clic su **[!UICONTROL Salva]**.

   ![&quot;Messaggistica push in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Ripeti i passaggi da 1 a 4 e crea elementi di dati per *Last Entered POI Latitude*, *Last Entered POI Longitude*, e *Last Entered POI Radius*.

Oltre agli elementi dati per Places Service, assicurati di creare elementi dati core per dispositivi mobili per *ID app* e *ID Experience Cloud*.

## Creare una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole di Experience Platform Launch consentono di creare flussi di lavoro complessi e con più soluzioni basati su attivatori di eventi. Con le regole, puoi creare nuove regole o modificare quelle esistenti e distribuire dinamicamente gli aggiornamenti nelle app mobili. Nell’esempio seguente, la regola viene attivata quando un utente accede a un POI delimitato da geotargeting. Dopo l’attivazione della regola, viene inviato un aggiornamento a Campaign Standard per registrare una voce in un POI specifico per un particolare utente in base all’ID Experience Cloud.

1. Nella proprietà di Experienci Platform Launch Mobile, nella scheda **[!UICONTROL Regole]**, fai clic su **[!UICONTROL Aggiungi regola]**.
1. Nella sezione **[!UICONTROL Events]**, fai clic su **[!UICONTROL +]** e seleziona **[!UICONTROL Places Service]** come estensione.
1. Per **[!UICONTROL Tipo evento]**, seleziona **[!UICONTROL Inserisci POI]**.
1. Denomina la regola, ad esempio **L&#39;utente ha immesso un POI**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.
1. Lascia vuota la sezione **[!UICONTROL Conditions]**.

   Questa sezione ti consente di filtrare o porre restrizioni su quando attivare questa regola.

1. Nella sezione **[!UICONTROL Azioni]** fare clic su **[!UICONTROL +]**.
1. Nell&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]** e nell&#39;elenco a discesa **[!UICONTROL Tipo azione]**, seleziona **[!UICONTROL Invia postback]**.
1. In **[!UICONTROL URL]**, devi costruire l&#39;endpoint delle posizioni Campaign Standard.

   L&#39;URL deve essere simile a `https:///rest/head/mobileAppV5//locations/`.
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
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

>[!IMPORTANT]
>
>* Potrebbe essere utile impostare un hook web di Slack come azione aggiuntiva per convalidare l’attivazione delle voci e la raccolta dei dati corretti.
>* Ricorda di pubblicare le modifiche recenti nell&#39;app per assicurarti che la regola e tutti gli elementi dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, avvia di nuovo l’app mobile per ottenere gli aggiornamenti di configurazione più recenti.

## Utilizzare i dati sulla posizione per eseguire il targeting dei messaggi di Campaign

Ora che i dati sulla posizione sono compilati in Campaign, possiamo utilizzare i POI come strumento per segmenti di pubblico.

1. Nell&#39;istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Crea notifica push]**.
1. Per il tipo di notifica push, selezionare **[!UICONTROL Invia messaggio push ai profili di Campaign]**.
1. Fai clic su **[!UICONTROL Avanti]** e digita i dettagli generali.
1. Nella schermata Pubblico, fai clic su **[!UICONTROL Conteggio]** per determinare a quanti utenti stimati verrà inviata la notifica push.

   >[!TIP]
   >
   >In questo esempio, il conteggio sarà 3, perché sono presenti tre dispositivi installati su cui viene testata l’applicazione.

1. Nel riquadro a sinistra, espandi la scheda **[!UICONTROL Profilo]** e trascina il filtro **[!UICONTROL Posizione POI]** nell&#39;area principale.
1. Nella finestra del filtro POI, inserisci il nome esatto del POI di cui desideri eseguire il targeting.

   >[!TIP]
   >
   >Puoi effettuare selezioni aggiuntive per determinare il periodo di tempo trascorso dalla precedente visita dell’utente a questo POI.

   ![&quot;Messaggistica push 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Fai clic su **[!UICONTROL Conferma]**.
1. Esegui di nuovo il conteggio nella parte superiore per vedere come cambia la dimensione del pubblico.

   Se non vedi l&#39;aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessun dispositivo ha attivato una voce. In questa situazione diventa utile disporre del web hook di Slack, perché puoi visualizzare un elenco di voci POI da vari dispositivi di test.

1. Puoi trascinare altri filtri di posizione POI per includere più POI nel messaggio.
1. Fai clic su **[!UICONTROL Avanti]** per completare la creazione della notifica push per la consegna.

   ![&quot;Messaggistica push 3 in ACS&quot;](/help/assets/ACS_push3.png)

L’utilizzo di Places Service con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base alle entrate e alle uscite del recinto geografico. Questa integrazione ti aiuta a creare casi d’uso più personalizzati e contestuali.
