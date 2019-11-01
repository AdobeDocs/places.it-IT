---
title: Notifiche push
seo-title: Notifiche push
description: Questa sezione fornisce informazioni sull'utilizzo di Luoghi con notifiche push in Campaign Standard.
seo-description: 'Questa sezione fornisce informazioni sull''utilizzo di Luoghi con notifiche push in Campaign Standard. '
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# Notifiche push con il servizio di localizzazione della piattaforma Experience {#push-notifications}

In questa guida verrà illustrato come utilizzare le informazioni di geolocalizzazione storiche per eseguire il targeting delle notifiche push distribuite tramite Adobe Campaign Standard.

## Prerequisiti

Prima di iniziare, effettuate le seguenti operazioni:

* Accertati che sia configurata un’applicazione mobile con l’SDK di Adobe Experience Platform Mobile, inclusa l’estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integra l’SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile nell’app.
* Aggiungi l'estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard alla configurazione dell'app mobile.

* [Create un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI Luoghi.

* Abilita e installa l’estensione [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.


## Creazione di elementi di dati in Experience Platform Launch

Dopo aver verificato che le estensioni del servizio Places e Places Monitor for Location Service funzionino correttamente nell’applicazione, crea gli elementi dati in Experience Platform Launch. Gli elementi dati consentono di leggere le informazioni fornite dalle estensioni che arrivano tramite l'hub eventi Mobile SDK e fungono da alias per recuperare i dati dall'applicazione client. Per recuperare i dati dalle estensioni Luoghi e inviare le informazioni Luoghi a Campaign, devi creare alcuni elementi di dati.

Per creare un elemento dati:

1. Nella proprietà mobile Launch della piattaforma Experience, fai clic sulla **[!UICONTROL Data Elements]** scheda e poi su **[!UICONTROLAAggiungi elemento]** dati.
1. Nell'elenco a **[!UICONTROL Extension]** discesa, selezionare **[!UICONTROL Places]**.
1. Dall’elenco a **[!UICONTROL Data Element Type]** discesa, selezionate **[!UICONTROL Name]**.
1. Nel riquadro a destra è possibile selezionare **[!UICONTROL Current POI]** il nome del POI in cui si trova l’utente.

   **[!UICONTROL Last Entered]** recupera il nome del POI immesso per l’ultima volta dall’utente e **[!UICONTROL Last Exited]** fornisce il nome del POI che l’ultimo utente ha lasciato. In questo esempio, sarà selezionato **[!UICONTROL Last Entered]** e digitato un nome per l'elemento dati, ad esempio **[!UICONTROL Last Entered POI Name]** e facendo clic su **[!UICONTROL Save]**.

   !["Messaggi push in Campaign Standard"](/help/assets/ACS_Push1.png)

1. Ripetete i passaggi da 1 a 4 e create gli elementi di dati per l’ *ultima latitudine* POI inserita, l’ *ultima longitudine* POI inserita e l’ *ultimo raggio* POI inserito.

Oltre agli elementi di dati per il servizio Location, accertati di creare elementi di dati Mobile Core per l'ID ** app e l'ID ** Experience Cloud.

## Crea una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole in Experience Platform Launch consentono di creare flussi di lavoro complessi e con più soluzioni basati su attivatori di eventi. Con le regole, puoi creare nuove regole o modificarne quelle esistenti e distribuire dinamicamente gli aggiornamenti alle applicazioni mobili. Nell’esempio seguente, la regola viene attivata quando un utente immette un POI con geofrequenza. Dopo l'attivazione della regola, viene inviato un aggiornamento a Campaign Standard per registrare una voce a un POI specifico per un utente specifico in base all'Experience Cloud ID.

1. Nella proprietà Launch Mobile, nella **[!UICONTROL Rules]** scheda fare clic su **[!UICONTROL Add Rule]**.
1. Nella **[!UICONTROL Events]** sezione fare clic **[!UICONTROL +]** e selezionare **[!UICONTROL Places]** l'estensione.
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. Denominate la regola, ad esempio **Utente immesso POI**.
1. Fai clic su **[!UICONTROL Keep Changes]**.
1. Lasciate vuota la **[!UICONTROL Conditions]** sezione.

   Questa sezione consente di filtrare o limitare il momento in cui questa regola deve essere attivata.

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTROL +]**.
1. Nell'elenco a **[!UICONTROL Extension]** discesa, selezionare **[!UICONTROL Mobile Core]** e nell'elenco a **[!UICONTROL Action Type]** discesa selezionare **[!UICONTROL Send Postback]**.
1. In **[!UICONTROL URL]**, devi costruire l'endpoint delle posizioni di Campaign Standard.

   L’URL deve essere simile a `https:///rest/head/mobileAppV5//locations/`.
Assicurati di utilizzare gli elementi di dati corretti creati in precedenza per il server Campaign e per pKey.

1. Fate clic sulla casella per aggiungere un corpo del post e inviare quanto segue:

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

1. Assicurarsi di utilizzare gli elementi dati creati nella sezione precedente.
1. In **[!UICONTROL Content Type]**, digitare **[!UICONTROL application/json]**.
1. Fai clic su **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Potrebbe essere utile impostare un gancio Web Slack come azione aggiuntiva per verificare che le voci vengano attivate e che i dati corretti vengano raccolti.


>* Ricorda di pubblicare le modifiche recenti all'app per essere sicuro che la regola e tutti gli elementi di dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, è necessario avviare nuovamente l'applicazione mobile per ottenere gli aggiornamenti di configurazione più recenti.


## Utilizza i dati della posizione per eseguire il targeting dei messaggi campagna

Ora che abbiamo i dati sulla posizione popolati in Campaign, possiamo usare i POI come strumento per il segmento di pubblico.

1. Nell'istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Create Push Notification]**.
1. Per il tipo di notifica push, selezionate **[!UICONTROL Send push to Campaign profiles]**.
1. Fare clic **[!UICONTROL Next]** e digitare i dettagli generali.
1. Nella schermata Pubblico, fate clic **[!UICONTROL Count]** per determinare a quanti utenti stimati verrà inviata la notifica push.

   >[!TIP]
   >
   >In questo esempio, il conteggio sarà 3, perché ci sono tre dispositivi installati su cui l'applicazione viene testata.

1. Nel riquadro a sinistra, espandete la **[!UICONTROL Profile]** scheda e trascinate il **[!UICONTROL POI location]** filtro nell’area principale.
1. Nella finestra del filtro POI, inserite il nome esatto del POI di destinazione.

   >[!TIP]
   >
   >Potete effettuare ulteriori selezioni per determinare il periodo di tempo dalla precedente visita dell’utente a questo POI.

   !["Push messaging 2 in ACS"](/help/assets/ACS_push2.png)

1. Fai clic su **[!UICONTROL Confirm]**.
1. Eseguite nuovamente il conteggio nella parte superiore per vedere il cambiamento delle dimensioni del pubblico.

   Se non visualizzi l’aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessuna voce è stata attivata da un dispositivo. La presenza del gancio per la rete Slack diventa preziosa in questa situazione, perché potete vedere un elenco di voci POI da vari dispositivi di prova.
1. Potete trascinare altri filtri di posizione POI per includere più POI nel messaggio.
1. Fate clic **[!UICONTROL Next]** per completare la creazione della notifica push per la consegna.

   !["Messaggi push 3 in ACS"](/help/assets/ACS_push3.html)

L'utilizzo di Location Service con Adobe Campaign Standard vi offre un potente strumento per segmentare e indirizzare i messaggi agli utenti in base a entrate ed uscite specifiche. Questa integrazione consente di creare casi di utilizzo più personalizzati e contestuali.