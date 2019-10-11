---
title: Utilizzo di Luoghi con Adobe Campaign Standard
seo-title: Utilizzo di Luoghi con Adobe Campaign Standard
description: Conoscere le preferenze e le abitudini dei clienti è fondamentale per qualsiasi campagna di marketing di successo. Sapere se un utente ha visitato una posizione fisica può anche aggiungere un contesto molto prezioso per formare una relazione con il consumatore.
seo-description: Conoscere le preferenze e le abitudini dei clienti è fondamentale per qualsiasi campagna di marketing di successo. Sapere se un utente ha visitato una posizione fisica può anche aggiungere un contesto molto prezioso per formare una relazione con il consumatore.
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Utilizzo di Luoghi con Adobe Campaign Standard {#places-with-acs}

*Grazie per averci visitato la settimana scorsa, siamo lieti di darvi una sorpresa da usare per la vostra prossima visita!*

Conoscere le preferenze e le abitudini dei clienti è fondamentale per qualsiasi campagna di marketing di successo. Gli elementi cercati da un utente e la cronologia degli acquisti precedenti svolgono un ruolo importante nel targeting delle audience. Sapere se un utente ha visitato una posizione fisica può anche aggiungere un contesto molto prezioso per formare una relazione con il consumatore.

Secondo una recente relazione di eMarketer, l'85% dei retailer che hanno conseguito risultati di alto livello crede che la posizione sia molto importante per le attività di marketing. Inoltre, oltre il 58% dei retailer del Nord America ha intenzione di investire nelle tecnologie di prossimità/localizzazione per migliorare le esperienze dei clienti.

![](/help/assets/using-loc-services-acs_0.png)

Pensa a quanto la posizione critica è nella tua esperienza di utilizzo smartphone. Quanto spesso chiedere al vostro smartphone di trovare ristoranti vicini, stazioni di benzina, negozi di alimentari o altri servizi.

Ha quindi senso che, come marchio, si dovrebbe pensare a come sfruttare la posizione nelle campagne di marketing. In questa guida ti mostreremo come sfruttare le potenzialità del servizio di localizzazione di Adobe Experience Platform per aggiungere contesto di posizione ai messaggi tramite Adobe Campaign Standard, consentendo di distribuire notifiche push o messaggi in-app personalizzati in base alla voce relativa ai punti di interesse storici.

Prima di iniziare, questa guida presuppone che sia configurata un'applicazione mobile con l'SDK di Adobe Experience Platform Mobile con l'estensione Adobe Campaign Standard. Oltre all’SDK di Adobe Experience Platform Mobile e a Campaign Standard, devi avere accesso a Experience Platform Location Service.

## Prerequisiti 

1. Integra l’SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile nell’app.
1. Aggiungi l'estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard alla configurazione dell'app mobile.
1. [Create uno o più POI](/help/places-database-management-1/managing-pois-in-the-places-ui.md).

>[!TIP]
>
>Se state cercando modi per caricare o gestire i POI in massa, consultate questo [script per caricare i POI da un file CSV](https://github.com/adobe/places-scripts) . Inoltre, le API [Places](/help/places-rest-apis/api-usage/api-usage.md) possono essere utilizzate per creare o gestire i punti di interesse.

Se non avete accesso a Luoghi, potete [richiedere l'accesso qui](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Abilitare e installare le estensioni Luoghi nella vostra applicazione

Dopo aver creato punti di interesse nell'interfaccia Luoghi, dovrete aggiungere la funzionalità Luoghi all'applicazione.

1. Seguire le istruzioni per abilitare le estensioni Places e Places Monitor nell'applicazione.
1. Nell’estensione Luoghi, accertati di aver selezionato la libreria appropriata di POI creata in precedenza.

   È possibile aggiungere altre librerie alla configurazione dell'estensione in qualsiasi momento.

1. Accertati di aver aggiunto queste configurazioni a una libreria e pubblicato le modifiche alla configurazione in Launch.
1. Nella scheda Ambienti **[di avvio]** UICONTROL, fai clic sull'icona delle istruzioni di installazione per visualizzare le istruzioni su come scaricare i file CocoaPod e Gradle appropriati nel progetto dell'app.
1. Nell’applicazione, seguire le istruzioni per aggiungere la modalità di sfondo Posizione all’applicazione e avviare il Monitor posizione luoghi.
1. Eseguite un test dell'applicazione tramite un simulatore di dispositivi per visualizzare la richiesta dell'applicazione nei punti di interesse vicini in base allo spoofing della posizione del dispositivo.

### Creazione di elementi dati in Experience Platform Launch

Dopo aver verificato che le estensioni Places e Places Monitor funzionino correttamente nell’applicazione, crea elementi di dati in Experience Platform Launch per leggere le informazioni fornite dalle estensioni e che arrivano tramite Mobile SDK event hub. Gli elementi dati agiscono essenzialmente come alias per recuperare i dati dall'applicazione client. Create alcuni elementi di dati per recuperare dati dalle estensioni Luoghi.

1. Nella proprietà mobile Launch della piattaforma Experience, nella **[!UICONTROL Data Elements]** scheda e fai clic su **[!UICONTROL Add Data Element]**.
1. Dal menu delle estensioni, selezionate **[!UICONTROL Places]**.
1. Dall'elenco a **[!UICONTROL Data Element]** discesa, selezionare **[!UICONTROL Name}**.
1. Nella finestra a destra, potete selezionare **[!UICONTROL Current POI]** quale recupererà il nome del POI in cui si trova l’utente.

   * **[!UICONTROL Last Entered]** recupera il nome del POI immesso per l’ultima volta dall’utente
   * **[!UICONTROL Last Exited]** specifica il nome del POI che l’utente ha lasciato per ultimo.

1. Seleziona **[!UICONTROL Last Entered]**.
1. Digitare un nome per l'elemento dati, ad esempio **[!UICONTROL Last Entered POI Name]**, e fare clic su **[!UICONTROL Save]**.


   ![](/help/assets/using-loc-services-acs_1.png)

1. Ripetete gli stessi passaggi e create gli elementi di dati per l’ *ultima latitudine* POI inserita, l’ *ultima longitudine* POI inserita, l’ *ultimo raggio* POI inserito.

Oltre agli elementi di dati per Luoghi, accertati di aver creato anche elementi di dati Mobile Core per l'ID ** app e l'ID ** Experience Cloud.

### Crea una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole in Experience Platform Launch consentono di creare flussi di lavoro complessi con più soluzioni basati su attivatori di eventi. Potete crearne di nuovi o apportare modifiche alle regole esistenti e distribuire gli aggiornamenti in modo dinamico alle applicazioni mobili. In questo esempio, creeremo una regola che viene attivata quando un utente accede a un POI con geofrequenza. Dopo l’attivazione della regola, viene inviato un aggiornamento a Campaign Standard per registrare una voce in un POI specifico per l’utente. Questo POI si basa su Experience Cloud ID.

1. Nella proprietà mobile Launch della piattaforma Experience, fai clic sulla **[!UICONTROL Rules]** scheda e poi su **[!UICONTROL Add Rule]**.
1. Nella **[!UICONTROL Events]** sezione fare clic **[!UICONTROL +]** e selezionare **[!UICONTROL Places]**.
1. In **[!UICONTROL Event Type]**, selezionate **[!UICONTROL Enter POI]**.
1. Immettete un nome per la regola, ad esempio **[!UICONTROL User entered POI]**.
1. Fai clic su **[!UICONTROL Keep Changes]**.
1. Lasciate vuota la **[!UICONTROL Conditions]** sezione.

   Questa sezione consente di filtrare o limitare il momento in cui questa regola deve essere attivata.

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. In **[!UICONTROL Extension]**, selezionate **[!UICONTROL Mobile Core]** e, in **[!UICONTROL Action Type]**, selezionate **[!UICONTROL Send Postback]**.

1. Per l'URL, devi creare l'endpoint delle posizioni Campaign Standard.

   L’URL deve essere simile a quello riportato di seguito. Assicurati di utilizzare gli elementi di dati corretti creati in precedenza per il server Campaign e per pKey.

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. Fate clic sulla casella per aggiungere un corpo del post e inviare quanto segue:

   ```text
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

1. Utilizzare gli elementi dati specifici creati nella sezione precedente.
1. In **[!UICONTROL Content Type]**, digitare **[!UICONTROL application/json]**.
1. Fate clic **[!UICONTROL Keep Changes]** dopo aver configurato questa impostazione.

   Potrebbe essere utile impostare un gancio Web di Slack come azione aggiuntiva per verificare che l'azione venga attivata e che vengano raccolti i dati corretti.

   >[!IMPORTANT]
   >
   >Ricorda di pubblicare le modifiche recenti all'app per essere sicuro che la regola e tutti gli elementi di dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, riavvia l’applicazione mobile per ottenere gli aggiornamenti di configurazione più recenti.

### Usa dati sulla posizione per eseguire il targeting dei messaggi Campaign Standard

Ora che abbiamo i dati sulla posizione popolati in Campaign, possiamo utilizzare i punti di interesse come strumento per il segmento di pubblico.

1. All'interno dell'istanza di Adobe Campaign Standard, fai clic su **[UICONTROL Crea notifica]** push.
1. Per il tipo di notifica push, selezionate **[UICONTROL Invia push agli abbonati]** all'app.

   Questo tipo di push verrà utilizzato per tutti gli utenti dell'applicazione. Se i tuoi utenti mobili sono collegati a un profilo Campaign, puoi anche selezionare **[UICONTROL Invia push ai profili]** Campaign i.

1. Fare clic **[!UICONTROL Next]** e digitare i dettagli generali nella schermata successiva.
1. Nella schermata Pubblico, fate clic **[!UICONTROL Count]** per vedere quanti utenti stimati verrà inviata la notifica push.

   In questo caso, il numero è tre, in quanto ci sono tre dispositivi installati nell'applicazione di prova.

1. Nella barra laterale sinistra, espandete la **[!UICONTROL Profile]** scheda e trascinate il **[!UICONTROL POI location]** filtro sull’area principale.
1. Nella finestra del filtro POI, inserite il nome esatto del POI di cui desiderate eseguire il targeting.

   Potete effettuare ulteriori selezioni per determinare l’intervallo di tempo dall’ultima visita dell’utente a questo POI.

   ![](/help/assets/using-loc-services-acs_2.png)

1. Fai clic su [!**Conferma]UICONTROL**.
1. Eseguite nuovamente il conteggio nella parte superiore per vedere il cambiamento delle dimensioni del pubblico.

   Se non visualizzi l’aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessun dispositivo ha attivato una voce. Qui è dove l'amo Slack diventa prezioso, come potete vedere un elenco di voci POI da vari dispositivi di prova.
1. Potete trascinare altri filtri di posizione POI per includere più POI nel messaggio.
1. Fate clic **[!UICONTROL Next]** per completare la creazione della notifica push per la consegna.

   ![](/help/assets/using-loc-services-acs_3.png)

Oltre alle notifiche push, puoi anche utilizzare i dati sulla posizione per segmentare gli utenti a cui desideri ricevere un messaggio in-app.

1. Nell'istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Create In-App message]**.
1. Selezionare il tipo di messaggio **[!UICONTROL Target all users of a Mobile application]**.
1. Fare clic **[!UICONTROL Next]** e digitare i dettagli generali nella schermata successiva.
1. Nel riquadro a sinistra, verifica di poter utilizzare diversi attivatori relativi a Places.
1. Se l’utente ha inserito un limite geografico POI, potete scegliere di visualizzare il messaggio in-app.

   Potete anche utilizzare i metadati definiti nell'interfaccia utente Luoghi per filtrare il pubblico. In questo esempio, desidero attivare un messaggio in-app mostrato solo agli utenti che sono usciti l’ultima volta da un POI che aveva anche una struttura Gym. Forse voglio mandare loro un sondaggio per vedere se hanno usato o meno la palestra.

1. Fai clic **[!UICONTROL Next]** per terminare la creazione del messaggio in-app da consegnare.

   ![](/help/assets/using-loc-services-acs_4.png)

L'utilizzo di Luoghi con Adobe Campaign Standard offre uno strumento molto potente per segmentare e indirizzare i messaggi agli utenti in base alla posizione storica. Questa semplice integrazione apre le porte a casi di utilizzo più personalizzati e contestuali.

Stiamo costantemente migliorando Luoghi e soluzioni integrate per portare il contesto della posizione nei flussi di lavoro mobili. Un prodotto che sfrutterà i vantaggi di Places è la prossima soluzione di Triggered Journey che consentirà ai clienti di creare flussi di lavoro in tempo reale basati su attivatori dell'evento come la posizione.

## Collegamenti consigliati

Per ulteriori informazioni, consulta:

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [Iscriviti per accedere ad Adobe Places Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Integrazione di Adobe Campaign con l’SDK della piattaforma Experience](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
