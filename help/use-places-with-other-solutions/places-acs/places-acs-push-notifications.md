---
title: Notifiche push
seo-title: Notifiche push
description: Questa sezione fornisce informazioni sull'utilizzo di Luoghi con notifiche push in Campaign Standard.
seo-description: 'Questa sezione fornisce informazioni sull''utilizzo di Luoghi con notifiche push in Campaign Standard. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Notifiche push con il servizio di localizzazione della piattaforma Experience {#push-notifications}

In questa guida verrà illustrato come utilizzare le informazioni di geolocalizzazione storiche per eseguire il targeting delle notifiche push distribuite tramite Adobe Campaign Standard.

>[!IMPORTANT]
>
>Prima di iniziare, effettuate le seguenti operazioni:
>
>* Accertati che sia configurata un’applicazione mobile con l’SDK di Adobe Experience Platform Mobile, inclusa l’estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Integra l’SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile nell’app.
>* Aggiungi l'estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard alla configurazione dell'app mobile.
   >
   >
* [Create un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI Luoghi.
   >
   >
* Abilita e installa l’estensione [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.



## Creazione di elementi di dati in Experience Platform Launch

Dopo aver verificato che le estensioni del servizio Places e Places Monitor for Location Service funzionino correttamente nell’applicazione, crea gli elementi dati in Experience Platform Launch. Gli elementi dati consentono di leggere le informazioni fornite dalle estensioni che arrivano tramite l'hub eventi Mobile SDK e fungono da alias per recuperare i dati dall'applicazione client. Creiamo alcuni elementi di dati per recuperare dati dalle estensioni Luoghi, in modo da poter inviare le informazioni Luoghi a Campaign.

1. Nella proprietà mobile Launch della piattaforma Experience, fai clic sulla scheda **Elementi** dati e quindi su **Aggiungi elemento** dati.
2. Nell’elenco a discesa **Estensione** , selezionate **Luoghi**.
3. Dall'elenco a discesa Tipo **elemento** dati, selezionare **Nome**.
4. Nel riquadro a destra, potete selezionare **POI** correnti che recupera il nome del POI in cui si trova l’utente.

   **Ultimo inserimento** recupera il nome del POI immesso dall’utente per ultimo, mentre **Ultima uscita** indica il nome del POI che l’utente ha lasciato per ultimo. In questo esempio, selezioneremo **Ultimo inserimento** e immetteremo un nome per l’elemento dati, ad esempio **Ultimo inserimento del nome** POI e faremo clic su **Salva**.

   !["Messaggi push in Campaign Standard"](/help/assets/ACS_Push1.png)


5. Ripetete gli stessi passaggi e create gli elementi di dati per l’ _ultima latitudine_ POI inserita, l’ _ultima longitudine_ POI inserita e l’ _ultimo raggio_ POI inserito.

Oltre agli elementi di dati per il servizio Location, accertati di creare elementi di dati Mobile Core per l'ID __ app e l'ID __ Experience Cloud.

## Crea una regola per inviare i dati sulla posizione ad Adobe Campaign Standard

Le regole in Experience Platform Launch consentono di creare flussi di lavoro complessi e con più soluzioni basati su attivatori di eventi. La cosa bella delle regole è che puoi creare nuove regole o modificarne quelle esistenti e distribuire gli aggiornamenti in modo dinamico alle applicazioni mobili. In questo esempio creeremo una regola che verrà attivata quando un utente immette un POI delimitato da aree geografiche. Dopo l’attivazione della regola, viene inviato un aggiornamento a Campaign per registrare una voce a un POI specifico per un utente specifico in base all’Experience Cloud ID.

1. Nella proprietà Launch mobile fare clic sulla scheda **Regole** e quindi su **Aggiungi regola**.
2. Nella sezione **Eventi** , fate clic su **+** e selezionate **Luoghi** come estensione.
3. Per Tipo **** evento, selezionate **Inserisci POI**.
4. Denominate la regola, ad esempio **Utente immesso POI**.
5. Click **Keep Changes**.
6. La sezione **Condizioni** consente di filtrare o limitare il momento in cui questa regola deve essere attivata.  Per ora lasceremo questo vuoto.
7. Nella sezione **Azioni** fare clic su **+** per creare una nuova azione
8. Nell’elenco a discesa **Estensione** , selezionate **Mobile Core,** quindi nell’elenco a discesa Tipo **** azione, selezionate **Invia postback**.
9. Per l' **URL**, devi creare l'endpoint delle posizioni di Campaign Standard.  L’URL deve essere simile a quello riportato di seguito. Assicurati di utilizzare gli elementi di dati corretti creati in precedenza per il server Campaign e per pKey. `https:///rest/head/mobileAppV5//locations/`
10. Fate clic sulla casella per aggiungere un corpo del post e inviare quanto segue:

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

11. Assicurarsi di utilizzare gli elementi dati specifici creati nella sezione precedente.
12. In Tipo **di** contenuto, digitate **application/json**.
13. Fare clic su **Mantieni modifiche** dopo aver configurato questa impostazione.
14. Può essere utile avere un gancio Web Slack impostato come azione aggiuntiva per verificare che le voci vengano attivate e che i dati corretti vengano raccolti.


>Non dimenticare di pubblicare le modifiche recenti nell'app per essere certi che la regola e tutti gli elementi di dati siano distribuiti come parte della configurazione. Dopo la pubblicazione, è necessario avviare nuovamente l'applicazione mobile per ottenere gli aggiornamenti di configurazione più recenti.

## Utilizza i dati della posizione per eseguire il targeting dei messaggi campagna

Ora che abbiamo i dati sulla posizione popolati in Campaign, possiamo usare i POI come strumento per il segmento di pubblico.

1. Nell'istanza di Adobe Campaign Standard, fai clic su **Crea notifica** push.
2. Per il tipo di notifica push, selezionate **Invia push ai profili** campagna.
3. Fare clic su **Avanti** e digitare i dettagli generali nella schermata successiva.
4. Nella schermata Pubblico, fate clic su **Conteggio** per vedere quanti utenti stimati verrà inviata la notifica push.

   *In questo caso, il mio conteggio sarà pari a tre, poiché ho tre dispositivi installati in cui testare l'applicazione.*

5. Nella barra laterale sinistra, espandete la scheda **Profilo** e trascinate il filtro posizione **** POI sull’area principale
6. Nella finestra del filtro POI, inserite il nome esatto del POI di destinazione.

   *Potete effettuare ulteriori selezioni per determinare l’intervallo di tempo dall’ultima visita dell’utente a questo POI.*

   !["Push messaging 2 in ACS"](/help/assets/ACS_push2.png)


7. Fate clic su **Conferma**.
8. Eseguite nuovamente il conteggio nella parte superiore per vedere il cambiamento delle dimensioni del pubblico.  Se non visualizzi l’aggiornamento del conteggio, potresti aver inserito un nome POI per il quale nessuna voce è stata attivata da un dispositivo. Qui è dove l'aggancio per il Web Slack diventa prezioso, perché potete vedere un elenco di voci POI da vari dispositivi di prova.
9. Potete trascinare altri filtri di posizione POI per includere più POI nel messaggio.
10. Fate clic su **Avanti** per completare la creazione della notifica push per la consegna.

   !["Messaggi push 3 in ACS"](/help/assets/ACS_push3.html)

L'utilizzo di Location Service con Adobe Campaign Standard vi offre un potente strumento per segmentare e indirizzare i messaggi agli utenti in base a voci ed entità specifiche. Questa semplice integrazione apre le porte a casi di utilizzo più personalizzati e contestuali.