---
title: Test e convalida del servizio Places
description: Questa sezione fornisce informazioni su come verificare e convalidare il servizio Places.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations per testare il servizio Places {#test-validate-loc-svc}

Molti clienti e organizzazioni definiranno i punti di interesse in tutto il mondo, pertanto è importante disporre di un modo per simulare e verificare il modo in cui il servizio Places interagisce con la tua applicazione. Queste informazioni sono utili per comprendere come verificare e convalidare le voci e le uscite del servizio Places che vengono attivate correttamente in base ai POI definiti e alla posizione corrente di un utente.

Poiché le variabili ambientali possono essere un fattore di segnale di posizione e precisione, abbiamo consigliato di stabilire prima i risultati di base lavorando localmente con strumenti per sviluppatori e voci di posizione simulate. L’obiettivo è quello di verificare che tutti gli eventi di posizione funzionino correttamente. Una volta convalidati correttamente gli eventi di posizione, è possibile testare le integrazioni della soluzione (ad esempio Analytics, Target e Campaign). Per facilitare le attività di test, è necessario impostare gli Slack Webhook con un postback e caricare i file GPX nel proprio ambiente di sviluppo individuale.

>[!IMPORTANT]
>
>Questo piano presuppone che siano stati creati dei punti di interesse nel [Interfaccia utente di Places Service](https://places.adobe.com) e le versioni più recenti dell’estensione Places vengono installate e configurate correttamente. Se si esegue il monitoraggio di un&#39;area attiva, si presuppone anche che venga implementata una soluzione di monitoraggio di area. Per ulteriori informazioni, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS, oppure [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing).

| Passaggio | Descrizione | Risultato previsto |
|--- |--- |--- |
| 1 | Conferma che siano state inserite le chiavi manifest corrette affinché Android conceda l&#39;accesso alla posizione del tracciamento. | Confermato |
| 1 bis | Conferma la configurazione degli aggiornamenti della posizione in iOS. Assicurati anche di disporre della configurazione appropriata delle chiavi plist in iOS per richiedere l&#39;autorizzazione dell&#39;utente per tenere traccia della posizione. | Confermato |
| 2 | Conferma quale modalità di monitoraggio è impostata per iOS. La modalità continua consente una maggiore precisione e persistenza, ma anche una maggiore durata della batteria. | Cambiamenti significativi o continui |
| 3 | Se utilizzi più di una libreria POI, verifica che le librerie appropriate siano state selezionate, ad Experience Platform Launch, nell’estensione Luoghi. | Confermato |
| 4 | Conferma che le versioni più recenti delle estensioni Mobile Core e Places siano state unite all’app tramite Gradle o CocoaPods. | Confermato: per ulteriori informazioni sugli aggiornamenti recenti, consulta la sezione [note sulla versione.](/help/release-notes.md) |
| 5 | Verifica che gli ambienti corretti siano configurati per il test. L’ID dell’ambiente Launch deve corrispondere all’ambiente di sviluppo Launch. | Confermato |
| 6 | Crea file GPX per ogni POI che desideri testare. I file GPX possono essere utilizzati in ambiente di sviluppo locale per simulare una voce di posizione. Per informazioni sulla creazione e l&#39;utilizzo di file GPX, consulta quanto segue: <br>[File GPX per iOS Simulator [chiuso]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[VERIFICA DELLA POSIZIONE NELLE APP MOBILI](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | I file GPX vengono creati e caricati nel progetto dell’app. |
| 7 | Senza fare altro, dovresti essere in grado di avviare l&#39;applicazione da Android Studio o XCode e vedere l&#39;avviso appropriato per richiedere l&#39;accesso per il percorso di tracciamento. Fai clic sul pulsante *Consenti sempre* autorizzazione.<br><br>È consigliabile utilizzare un dispositivo reale collegato al computer invece di utilizzare un simulatore di dispositivo. | Il prompt della richiesta di posizione deve essere visualizzato su un&#39;applicazione caricata tramite IDE |
| 8 | Una volta accettata l’autorizzazione Posizione . L’SDK di Places recupererà la posizione corrente del dispositivo e il codice di monitoraggio della regione dovrebbe iniziare a monitorare i 20 punti di interesse più vicini dalla posizione corrente | Vedere il campione di log sotto la tabella. |
| 9 | Il passaggio da una posizione all&#39;altra nello studio XCode o Android dovrebbe produrre eventi di ingresso per POI specifici. Al momento dell’accesso a un POI sono previsti i seguenti registri. | Vedere il campione di log sotto la tabella. |
| 10 | Dopo che il monitoraggio della regione ha rilevato punti di interesse nelle vicinanze, è necessario verificare l’invio di ping-out della posizione. In Launch, crea una nuova regola che utilizza l’estensione Luoghi per attivarsi in base a una voce di recinto geografico. Quindi crea una nuova azione utilizzando Mobile Core per inviare un postback. La creazione di un&#39;app Slack Webhook ti aiuta a vedere le voci e le uscite di posizione. Per informazioni sulla creazione di un&#39;app Slack Webhook vedi [Invio di messaggi tramite Webhook in entrata.](https://api.slack.com/messaging/webhooks) |  |
| 10 bis | In Launch, accertati di aver aggiunto elementi dati per l’estensione Luoghi tra cui: <br>Nome POI corrente<br>Ultimo POI attuale<br>Tempo POI corrente<br>Ultimo nome inserito<br>Ultimo inserimento<br>Ultimo ingresso lungo<br>Ultimo nome uscito<br>Ultimo ultimo arrivato<br>Ultima uscita lunga<br>Timestamp |  |
| 10 ter | Crea una nuova regola con un evento = Luoghi → Inserisci POI |  |
| 10c | Crea un&#39;azione = Mobile Core → Postback |  |
| 10 quinquies | Utilizza l’URL Webhook per l’app Slack, ad esempio https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10 sexies | Il corpo del post sarebbe simile a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Assicurati di utilizzare gli elementi dati specifici creati qui. |  |
| 10 septies | Assicurati di pubblicare tutti i nuovi elementi dati e le modifiche alle regole in Launch. Seleziona una libreria di sviluppo funzionante in alto a destra nell’interfaccia Launch. |  |
| 11 | Avvia e verifica di nuovo l’applicazione sfogliando tra le posizioni GPX nell’IDE sviluppatore. | Ora dovresti vedere le notifiche di Slack che mostrano le voci per ogni POI quando selezioni diverse posizioni nell&#39;ambiente di sviluppo. |
|  | **PUNTO DI RIEPILOGO RAPIDO**<br> Tutti questi test possono essere condotti localmente senza dover passare a una posizione POI specifica. Il test di convalida consente di verificare che l&#39;applicazione sia configurata correttamente e abbia ricevuto le autorizzazioni corrette per il percorso. <br><br>Questa convalida ti assicura inoltre che i punti di interesse definiti funzionino correttamente con l’implementazione del monitoraggio dell’area.  Dopo questo passaggio, inizieremo a testare i messaggi in Campaign per vedere se i messaggi corretti vengono visualizzati in base alle entrate e alle uscite dei punti di interesse. |  |
|  | **Verifica della messaggistica in-app Adobe Campaign Standard con Places Service.** |  |
| 12 | Nel dashboard Campaign principale configura un nuovo messaggio in-app (tipo = trasmissione) |  |
| 12 bis | In trigger, seleziona **Places event type (Tipo di evento): voce come attivatore**. |  |
| 12 ter | Seleziona **[!UICONTROL Posiziona metadati personalizzati]** come filtro aggiuntivo - usa tipo POI = Last Entered POI (POI ultimo inserito).<br>Usiamo **[!UICONTROL Ultimo inserimento]** come tipo di POI perché nella maggior parte dei casi, **[!UICONTROL Ultimo inserimento]** sarà uguale a **[!UICONTROL POI attuale]**. <br><br>**[!UICONTROL POI attuale ]**Deve essere utilizzato solo nei casi in cui ci sono dei recinti geografici POI sovrapposti. In questo caso, questi punti di interesse devono essere classificati e quindi i**[!UICONTROL  POI attuale ]**mostrerà il punto di interesse di primo livello tra i 2 o i 3 recinti geografici in cui potrebbe trovarsi attualmente un utente. |  |
| 12c | Seleziona una chiave di metadati personalizzata che ti aiuterà a limitare quali punti di interesse riceveranno un messaggio. |  |
| 12 quinquies | Per frequenza e durata, mantieni a uno o due giorni, in modo che se non ti piacciono i criteri, puoi scadere il trigger in un periodo di tempo più breve. |  |
| 12 sexies | Per click-through Always/Once o Fino a , seleziona *SEMPRE* in modo da poter eseguire test in più posizioni. | Un messaggio in-app viene visualizzato SEMPRE quando simula un cambiamento di posizione che soddisfa i criteri di metadati appropriati. |
| 12 septies | Per la visualizzazione, selezionare un&#39;opzione diversa da Notifica locale. Questo rende più facile vedere quando si esegue un test con l’app in primo piano.) |  |
| 12g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 13 | Nell’ambiente di sviluppo, per garantire che le nuove regole della campagna siano scaricate, esci e avvia di nuovo l’applicazione. | Non dimenticare che le applicazioni devono essere completamente avviate nuovamente per scaricare il nuovo file delle regole di Campaign sul dispositivo. |
| 14 | Nell&#39;applicazione di sviluppo, cambia posizione utilizzando i file GPX creati in precedenza. | Dovresti visualizzare il messaggio in-app in base ai criteri impostati in precedenza. |
| 15 | Per il test successivo, in sostanza copieremo gli stessi passaggi di prima, ma questa volta testeremo la NOTIFICA LOCALE. | Il risultato atteso è che le notifiche locali vengono visualizzate ogni volta che vengono soddisfatti i criteri di corrispondenza. |
| 16 | Configura un nuovo messaggio in-app (tipo = trasmissione). |  |
| 16 bis | In trigger, seleziona **[!UICONTROL Tipo di evento Luoghi]** - **[!UICONTROL Ingresso come trigger]**. |  |
| 16 ter | Seleziona i metadati personalizzati Luoghi come filtro aggiuntivo - utilizza **[!UICONTROL Tipo POI]** = **[!UICONTROL Ultimo POI inserito]**. |  |
| 16c | Seleziona una chiave di metadati personalizzata che ti aiuterà a limitare quali punti di interesse riceveranno un messaggio. |  |
| 16 quinquies | Per frequenza e durata, mantieni solo uno o due giorni, in modo che se non ti piacciono i criteri, puoi scadere il trigger in un periodo di tempo più breve. |  |
| 16 sexies | Per click-through Always/Once o Fino al click-through, **[!UICONTROL SEMPRE]**. |  |
| 16 septies | Per il tipo di visualizzazione, seleziona **[!UICONTROL Notifica locale]**. |  |
| 16g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 17 | Nell’ambiente di sviluppo, collega il dispositivo e premi **[!UICONTROL Play]** sulla build. Dopo aver stabilito che la posizione funziona, esegui in background l&#39;applicazione e continua a cambiare posizione in Xcode o Android Studio. Dovresti comunque visualizzare le lette della console che indicano la modifica della posizione e anche le notifiche locali visualizzate in base ai criteri impostati nel trigger. (Potrebbe esserci un ritardo di 1-2 secondi). | Il risultato atteso è che le notifiche locali vengono visualizzate ogni volta che i criteri corrispondenti vengono soddisfatti. |
|  | **PUNTO RIEPILOGO** <br>A questo punto, dovremmo vedere i punti di interesse nel nostro ambiente locale. Dovremmo anche visualizzare messaggi da Campaign basati sul lavoro POI. In caso di errori, controlla se una notifica di Slack non è uscita. Se non è presente alcun messaggio di Slack, controlla la console dell’applicazione, perché potrebbe non essere stata registrata una nuova voce di posizione. Se i risultati sono positivi, possiamo essere sicuri che l’applicazione funzioni correttamente e che anche il servizio di messaggistica Places e Campaign funzioni correttamente. |  |
|  | **TEST IN LOCO** <br>Non dovrebbe cambiare molto quando si esegue il test sulla posizione. Mantenere attivo il postback di slack dovrebbe aiutare a capire se il dispositivo sta ottenendo una voce e un&#39;uscita per la posizione. |  |
| 18 | Effettuare test con dispositivi che iniziano con wifi e cellulare disabilitato e quindi abilitarlo una volta nella regione POI. | Se si verifica un errore, ricorda se in Slack si riceve una voce di recinzione geografica e una notifica. Qual è la marca temporale nella notifica di Slack? |
| 19 | Effettuare il test con solo cellulare abilitato e con il wifi spento. |  |
| 20 | Eseguire test sia con cellulare che wifi acceso. |  |
|  | **PUNTO RIEPILOGO** <br>I test in loco devono corrispondere al test di sviluppo. Tieni presente che ci sono alcuni fattori ambientali che possono venire in gioco nel determinare la posizione degli utenti, come la durata del tempo trascorso in una recinzione geografica POI, la disponibilità di segnale cellulare e la forza dei punti di accesso wifi vicini. |  |

## Esempi di log

**Passaggio 8 :** Registri previsti di iOS e Android durante un aggiornamento della posizione

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Passaggio 9 :** Registri previsti di iOS e Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
