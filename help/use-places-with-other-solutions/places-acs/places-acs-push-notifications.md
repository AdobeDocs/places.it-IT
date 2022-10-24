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

In questa sezione viene illustrato come utilizzare le informazioni di geolocalizzazione storiche per eseguire il targeting delle notifiche push distribuite tramite Adobe Campaign Standard.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un’app mobile configurata con l’SDK di Adobe Experience Platform Mobile, tra cui [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrare le [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nell’app.
* Aggiungi il [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione dell’app mobile.

* [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI di Places Service.

* Abilita e installa la [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creare elementi dati in Experience Platform Launch

Dopo aver verificato che l&#39;estensione Places e una soluzione di monitoraggio regionale ([Documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS, oppure [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) funziona correttamente nell’applicazione, è necessario creare elementi dati in Experience Platform Launch. Gli elementi dati ti consentono di leggere le informazioni fornite dalle estensioni provenienti dall’hub eventi Mobile SDK e di fungere da alias per recuperare i dati dall’applicazione client. Per recuperare i dati dalle estensioni Luoghi e inviare le informazioni sul servizio Luoghi a Campaign, devi creare alcuni elementi di dati.

Per creare un elemento dati:

1. Nella proprietà mobile del Experience Platform Launch, fai clic sul pulsante **[!UICONTROL Elementi dati]** e fai clic su **[!UICONTROL Aggiungi elemento dati]**.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places Service]**.
1. Da **[!UICONTROL Tipo di elemento dati]** elenco a discesa, seleziona **[!UICONTROL Nome]**.
1. Nel riquadro a destra è possibile selezionare **[!UICONTROL POI attuale]** recupera il nome del POI in cui si trova attualmente l’utente.

   **[!UICONTROL Ultimo inserimento]** recupera il nome del POI immesso per l’ultima volta dall’utente, e **[!UICONTROL Ultimo uscita]** fornisce il nome del POI che l’utente ha lasciato per ultimo. In questo esempio abbiamo selezionato **[!UICONTROL Ultimo inserimento]** e ha digitato un nome per l&#39;elemento dati, ad esempio **[!UICONTROL Nome POI inserito per ultimo]** e su cui hai fatto clic **[!UICONTROL Salva]**.

   ![&quot;Messaggi push in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Ripeti i passaggi da 1 a 4 e crea elementi dati per *Latitudine ultimo POI inserito*, *Longitudine ultimo POI inserito* e *Raggio POI inserito per ultimo*.

Oltre agli elementi dati per Places Service, assicurati di creare elementi dati core per dispositivi mobili per *ID app* e *ID Experience Cloud*.

## Creare una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole del Experience Platform Launch consentono di creare flussi di lavoro complessi e con più soluzioni in base agli attivatori degli eventi. Con le regole, puoi creare nuove regole o modificarne quelle esistenti e distribuire gli aggiornamenti in modo dinamico alle tue applicazioni mobili. Nell’esempio seguente, la regola viene attivata quando un utente accede a un POI delimitato da una geolocalità. Dopo l’attivazione della regola, viene inviato un aggiornamento ad Campaign Standard per registrare una voce a un POI specifico per un utente specifico in base all’ID Experience Cloud.

1. Nella proprietà mobile del tuo Experience Platform Launch, **[!UICONTROL Regole]** scheda , fai clic su **[!UICONTROL Aggiungi regola]**.
1. Sotto la **[!UICONTROL Eventi]** sezione, fai clic su **[!UICONTROL +]** e seleziona **[!UICONTROL Places Service]** come estensione.
1. Per **[!UICONTROL Tipo evento]**, seleziona **[!UICONTROL Inserisci POI]**.
1. Denomina la regola, ad esempio: **POI immesso dall’utente**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.
1. Lascia la **[!UICONTROL Condizioni]** sezione vuota.

   Questa sezione ti consente di filtrare o impostare restrizioni su quando attivare questa regola.

1. Sotto la **[!UICONTROL Azioni]** sezione, fai clic su **[!UICONTROL +]**.
1. In **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Core mobile]** e **[!UICONTROL Tipo di azione]** elenco a discesa, seleziona **[!UICONTROL Invia postback]**.
1. In **[!UICONTROL URL]**, è necessario creare l’endpoint delle posizioni di Campaign Standard.

   L’URL deve essere simile a `https:///rest/head/mobileAppV5//locations/`.
Assicurati di utilizzare gli elementi dati corretti creati in precedenza per il server Campaign e per la chiave.

1. Fai clic sulla casella per aggiungere un corpo del post e invia quanto segue:

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
>* Potrebbe essere utile impostare un hook web di Slack come azione aggiuntiva per verificare che le voci vengano attivate e che vengano raccolti i dati corretti.
>* Ricorda di pubblicare le modifiche recenti nell&#39;app per essere certo che la regola e tutti gli elementi dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, avvia di nuovo l’app mobile per ottenere gli ultimi aggiornamenti di configurazione.


## Utilizzare i dati sulla posizione per eseguire il targeting dei messaggi di Campaign

Ora che i dati sulla posizione sono stati compilati in Campaign, possiamo utilizzare i POI come strumento per segmenti di pubblico.

1. Nella tua istanza Adobe Campaign Standard, fai clic su **[!UICONTROL Creare notifiche push]**.
1. Per il tipo di notifica push, seleziona **[!UICONTROL Inviare messaggi push ai profili Campaign]**.
1. Fai clic su **[!UICONTROL Successivo]** e digitare i dettagli generali.
1. Nella schermata Pubblico, fai clic su **[!UICONTROL Conteggio]** per determinare quanti utenti stimati verrà inviata la notifica push.

   >[!TIP]
   >
   >In questo esempio, il conteggio sarà 3, perché ci sono tre dispositivi installati su cui l&#39;applicazione viene testata.

1. Nel riquadro a sinistra, espandi il **[!UICONTROL Profilo]** e trascina **[!UICONTROL Posizione POI]** filtrare fino all&#39;area principale.
1. Nella finestra del filtro POI, immetti il nome esatto del POI di cui desideri eseguire il targeting.

   >[!TIP]
   >
   >Puoi effettuare selezioni aggiuntive per determinare il periodo di tempo dalla precedente visita dell’utente a questo POI.

   ![&quot;Messaggi push 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Fai clic su **[!UICONTROL Conferma]**.
1. Esegui di nuovo il conteggio nella parte superiore per vedere la modifica della dimensione del pubblico.

   Se non visualizzi l&#39;aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessuna periferica ha attivato una voce. Avere il gancio web di Slack diventa prezioso in questa situazione, perché è possibile vedere un elenco di voci POI da vari dispositivi di prova.

1. Puoi trascinare ulteriori filtri di posizione POI per includere più POI nel messaggio.
1. Fai clic su **[!UICONTROL Avanti]** per completare la creazione della notifica push per la consegna.

   ![&quot;Messaggi push 3 in ACS&quot;](/help/assets/ACS_push3.png)

L’utilizzo di Places Service con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base alle entrate e alle uscite del recinto geografico. Questa integrazione consente di creare casi d’uso più personalizzati e contestuali.
