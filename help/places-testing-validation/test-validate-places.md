---
title: Test e convalida di Places Service
description: In questa sezione vengono fornite informazioni su come verificare e convalidare Places Service.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 1%

---

# Recommendations per testare Places Service {#test-validate-loc-svc}

Molti clienti e organizzazioni definiranno i punti di interesse in tutto il mondo, pertanto è importante disporre di un modo per simulare e testare l’interazione del servizio Places con l’applicazione. Queste informazioni spiegano come verificare e convalidare le entrate e le uscite di Places Service che vengono attivate correttamente in base ai punti di interesse definiti e alla posizione corrente di un utente.

Poiché le variabili ambientali possono essere un fattore nel segnale di posizione e nell’accuratezza, è consigliabile per prima cosa stabilire i risultati della linea di base lavorando localmente con strumenti per sviluppatori e voci di posizione simulate. L’obiettivo è quello di verificare che tutti gli eventi di posizione funzionino correttamente. Dopo la corretta convalida degli eventi di posizione, è possibile testare le integrazioni della soluzione (ad esempio, Analytics, Target e Campaign). Per facilitare le attività di test, devi impostare dei webhook di Slack con un postback e caricare i file GPX nel tuo ambiente di sviluppo individuale.

>[!IMPORTANT]
>
>Questo piano presuppone che i punti di interesse siano stati creati nell&#39;interfaccia utente di [Places Service](https://places.adobe.com) e che le versioni più recenti dell&#39;estensione Places siano installate e configurate correttamente. Se si esegue il monitoraggio attivo dell&#39;area, si presuppone anche l&#39;implementazione di una soluzione di monitoraggio dell&#39;area. Per ulteriori informazioni, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS o [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing).

| Passaggio | Descrizione | Risultato previsto |
|--- |--- |--- |
| 1 | Verifica che siano state immesse le chiavi del manifesto corrette affinché Android possa concedere l’accesso al tracciamento della posizione. | Confermato |
| 1a | In iOS, conferma la configurazione degli aggiornamenti della posizione. Inoltre, assicurati di disporre delle chiavi di elenco appropriate in iOS per richiedere l’autorizzazione dell’utente per tenere traccia della posizione. | Confermato |
| 2 | Conferma quale modalità di monitoraggio è impostata per iOS. La modalità continua consente una maggiore precisione e persistenza, ma riduce anche notevolmente la durata della batteria. | Modifiche significative o continue |
| 3 | Se utilizzi più di una libreria POI, verifica che siano state selezionate le librerie appropriate nell&#39;estensione Luoghi per il Experience Platform Launch. | Confermato |
| 4 | Conferma che le versioni più recenti delle estensioni Mobile Core e Places siano state incluse nell’app tramite Gradle o CocoaPods. | Confermato. Per ulteriori informazioni sugli aggiornamenti recenti, consulta le [note sulla versione.](/help/release-notes.md) |
| 5 | Conferma che gli ambienti corretti siano configurati per il test. L&#39;ID dell&#39;ambiente di Launch deve corrispondere all&#39;ambiente di sviluppo Launch. | Confermato |
| 6 | Crea file GPX per ogni POI da testare. I file GPX possono essere utilizzati nell’ambiente di sviluppo locale per simulare una voce di percorso. Per informazioni sulla creazione e l&#39;utilizzo di file GPX, vedere: <br>[File GPX per iOS Simulator [chiusi]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[VERIFICA DELLA POSIZIONE NELLE APP MOBILI](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | I file GPX vengono creati e caricati nel progetto dell’app. |
| 7 | Senza fare altro, dovresti essere in grado di avviare l’applicazione da Android Studio o Xcode e visualizzare l’avviso appropriato per richiedere l’accesso al percorso di tracciamento. Fai clic sull&#39;autorizzazione *Consenti sempre*.<br><br>È consigliabile utilizzare un dispositivo reale connesso al computer anziché utilizzare il simulatore di dispositivi. | Il prompt della richiesta della posizione deve essere visualizzato nell&#39;applicazione caricata tramite IDE |
| 8 | Una volta accettata l’autorizzazione Posizione. L’SDK Luoghi recupererà la posizione corrente del dispositivo e il codice di monitoraggio della regione dovrebbe iniziare a monitorare i 20 punti di interesse più vicini dalla posizione corrente | Vedi l’esempio di registro sotto la tabella. |
| 9 | Il passaggio tra posizioni diverse in Xcode o Android studio dovrebbe produrre eventi di ingresso per punti di interesse specifici. I seguenti registri sono previsti al momento dell’ingresso in un POI. | Vedi l’esempio di registro sotto la tabella. |
| 10 | Una volta che il monitor della regione rileva i punti di interesse nelle vicinanze, devi eseguire il test inviando i ping della posizione. In Launch, crea una nuova regola che utilizza l’estensione Luoghi da attivare in base a una voce di recinto geografico. Quindi crea una nuova azione utilizzando Mobile Core per inviare un postback. La creazione di un&#39;app per webhook di Slack consente di visualizzare le entrate e le uscite della posizione. Per informazioni sulla creazione di un&#39;app per webhook di Slack, vedere [Invio di messaggi tramite webhook in ingresso.](https://api.slack.com/messaging/webhooks) |  |
| 10 bis | In Launch, accertati di aver aggiunto gli elementi dati per l&#39;estensione Places, tra cui: <br>Nome punto di interesse corrente<br>Lat punto di interesse corrente<br>Lungo punto di interesse corrente<br>Nome ultimo inserito<br>Ultimo inserito latitudine<br>Lungo ultimo inserito<br>Nome ultimo uscito<br>Ultimo uscito latitudine<br>Lungo ultimo ingresso<br>Timestamp |  |
| 10 ter | Crea una nuova regola con un Evento = Luoghi → Inserisci POI |  |
| 10 quater | Crea un’azione = Postback → core mobile |  |
| 10d | Utilizza l’URL del webhook per l’app di Slack, ad esempio https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD... |  |
| 10e | Il corpo del post sarà simile a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Assicurati di utilizzare gli elementi dati specifici creati qui. |  |
| 10f | Assicurati di pubblicare tutte le modifiche apportate al nuovo elemento dati e alla regola in Launch. (seleziona una libreria di sviluppo funzionante in alto a destra nell’interfaccia Launch). |  |
| 11 | Avvia e verifica nuovamente l’applicazione capovolgendo le posizioni GPX nell’IDE per sviluppatori. | Ora dovresti vedere le notifiche di Slack che mostrano le voci per ogni POI quando selezioni diverse posizioni nell&#39;ambiente di sviluppo. |
|  | **PUNTO DI RIEPILOGO RAPIDO**<br> Tutti questi test possono essere eseguiti localmente senza dover passare a una posizione POI specifica. I test di convalida garantiscono che l&#39;applicazione sia configurata correttamente e abbia ricevuto le autorizzazioni corrette per la posizione. <br><br>Questa convalida garantisce inoltre che i POI definiti funzionino correttamente con l&#39;implementazione del monitoraggio dell&#39;area geografica.  Dopo questo passaggio, inizieremo a testare i messaggi in Campaign per vedere se i messaggi corretti vengono visualizzati in base alle entrate e alle uscite dei POI. |  |
|  | **Verifica della messaggistica in-app di Adobe Campaign Standard con Places Service.** |  |
| 12 | Nel dashboard principale di Campaign configura un nuovo messaggio in-app (tipo = broadcast) |  |
| 12 bis | In trigger, selezionare **Tipo di evento Places - Voce come trigger**. |  |
| 12 ter | Seleziona **[!UICONTROL Posiziona metadati personalizzati]** come filtro aggiuntivo. Usa tipo POI = Ultimo POI inserito.<br>Come tipo di POI viene utilizzato **[!UICONTROL Ultimo immesso]** perché nella maggior parte dei casi **[!UICONTROL Ultimo inserito]** sarà uguale a **[!UICONTROL Punto di interesse corrente]**. <br><br>**[!UICONTROL Il punto di interesse corrente ]**deve essere utilizzato solo nelle istanze in cui sono presenti recinti geografici di interesse sovrapposti. In questo caso, questi POI devono essere CLASSIFICATI e poi il**[!UICONTROL  POI attuale ]**visualizzerà il POI classificato più in alto dei 2 o 3 recinti geografici in cui un utente potrebbe essere attualmente. |  |
| 12c | Seleziona una chiave di metadati personalizzata che ti aiuterà a limitare quali POI riceveranno un messaggio. |  |
| 12d | Per frequenza e durata, attendi solo a uno o due giorni, in modo che se non ti piace il criterio, puoi far scadere il trigger in un periodo di tempo più breve. |  |
| 12e | Per il click-through Always/Once o Until, selezionare *ALWAYS* in modo da poter eseguire il test in più posizioni. | Un messaggio in-app viene visualizzato SEMPRE quando simuli una modifica della posizione che soddisfa i criteri di metadati appropriati. |
| 12f | Per la visualizzazione, seleziona un’opzione diversa da Notifica locale. Questo consente di vedere più facilmente quando si esegue il test con l’app in primo piano.) |  |
| 12g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 13 | Nell’ambiente di sviluppo, per garantire che vengano scaricate nuove regole della campagna, esci e avvia di nuovo l’applicazione. | Non dimenticare che è necessario riavviare completamente le applicazioni affinché il nuovo file delle regole di Campaign possa essere scaricato sul dispositivo. |
| 14 | Nell’applicazione di sviluppo, cambia posizione utilizzando i file GPX creati in precedenza. | Il messaggio in-app dovrebbe apparire in base ai criteri impostati in precedenza. |
| 15 | Per il prossimo test, in sostanza copieremo gli stessi passaggi di prima, ma questa volta verificheremo LOCAL NOTIFICATION. | Il risultato atteso è che le notifiche locali vengono visualizzate ogni volta che vengono soddisfatti i criteri di corrispondenza. |
| 16 | Configura un nuovo messaggio in-app (tipo = broadcast). |  |
| 16 bis | Nei trigger, selezionare **[!UICONTROL Tipo di evento Luoghi]** - **[!UICONTROL Voce come trigger]**. |  |
| 16 ter | Seleziona i metadati personalizzati di Places come filtro aggiuntivo. Utilizza **[!UICONTROL Tipo POI]** = **[!UICONTROL Ultimo POI immesso]**. |  |
| 16c | Seleziona una chiave di metadati personalizzata che ti aiuterà a limitare quali POI riceveranno un messaggio. |  |
| 16d | Per frequenza e durata, mantieni solo uno o due giorni, in modo che se non ti piace il criterio, puoi far scadere il trigger in un periodo di tempo più breve. |  |
| 16e | Per il click-through Always/Once o Until, **[!UICONTROL ALWAYS]**. |  |
| 16f | Per il tipo di visualizzazione, selezionare **[!UICONTROL Notifica locale]**. |  |
| 16g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 17 | Nell&#39;ambiente di sviluppo, connetti il dispositivo e premi **[!UICONTROL Play]** sulla build. Una volta stabilito che la posizione funziona, esegui il background dell’applicazione e continua a cambiare posizione in Xcode o Android Studio. Dovresti comunque vedere le letture della console che indicano il cambiamento di posizione, e dovresti anche vedere le notifiche locali visualizzate a seconda dei criteri impostati nel trigger. (Potrebbe verificarsi un ritardo di 1-2 secondi). | Il risultato previsto è la visualizzazione di notifiche locali ogni volta che vengono soddisfatti i criteri di corrispondenza. |
|  | **SUMMARY POINT** <br>In questa fase, dovremmo visualizzare le voci POI nel nostro ambiente locale. Dovremmo anche visualizzare i messaggi provenienti da Campaign in base al lavoro POI. In caso di errori, verifica se non è stata inviata una notifica di Slack. Se non è presente alcun messaggio di Slack, controllare la console dell&#39;applicazione, perché è possibile che non sia stata registrata una nuova voce relativa al percorso. Se i risultati sono corretti, possiamo essere sicuri che l’applicazione funzioni correttamente e che anche il servizio di messaggistica di Places e Campaign funzioni correttamente. |  |
|  | **TEST IN LOCO** <br>Non dovrebbe cambiare molto durante il test sulla posizione. Mantenere attivo il postback di Slack dovrebbe aiutare a capire se il dispositivo sta ottenendo un ingresso e un&#39;uscita per la posizione. |  |
| 18 | Esegui i test con i dispositivi che iniziano con Wi-Fi e rete cellulare disabilitati e quindi abilita una volta nell’area POI. | In caso di errore, ricorda se ricevi una voce di recinto geografico e una notifica in Slack. Qual è la marca temporale nella notifica di Slack? |
| 19 | Eseguire il test con la sola rete cellulare attivata e con la rete Wi-Fi disattivata. |  |
| 20 | Eseguire il test con la rete cellulare e la rete Wi-Fi accese. |  |
|  | **SUMMARY POINT** <br>I test in loco devono corrispondere esattamente ai test di sviluppo. Tieni presente che alcuni fattori ambientali possono intervenire nella determinazione della posizione di un utente, come la durata del tempo trascorso in un recinto geografico POI, la disponibilità del segnale cellulare e la forza dei punti di accesso wifi vicini. |  |

## Esempi di registro

**Passaggio 8:** registri previsti di iOS e Android durante un aggiornamento della posizione

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Passaggio 9:** registri previsti di iOS e Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
