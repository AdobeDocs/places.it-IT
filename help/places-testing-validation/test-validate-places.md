---
title: Verifica e convalida dei luoghi
seo-title: Verifica e convalida dei luoghi
description: Questa sezione fornisce informazioni su come verificare e convalidare i luoghi.
seo-description: Questa sezione fornisce informazioni su come verificare e convalidare i luoghi.
translation-type: tm+mt
source-git-commit: 181185d441a6a4740b2e8770adcb71e81e2e816e

---


# Raccomandazioni per testare il servizio Location {#test-validate-loc-svc}

Molti clienti e organizzazioni definiranno i POI in tutto il mondo, pertanto è importante avere un modo per simulare e verificare in che modo il servizio di localizzazione interagisce con la vostra applicazione.

Queste informazioni sono utili per verificare e convalidare le voci e le uscite del servizio di localizzazione che vengono attivate correttamente in base ai POI definiti e alla posizione corrente di un utente.

Poiché le variabili ambientali possono essere un fattore di segnalazione e precisione della posizione, è consigliabile stabilire i risultati della linea di base prima lavorando localmente con gli strumenti di sviluppo e le voci di posizione simulate. L'obiettivo qui è convalidare il corretto funzionamento di tutti gli eventi di posizione.

Una volta convalidati correttamente gli eventi di posizione, è possibile sottoporre a test le integrazioni della soluzione (ad esempio, Analytics, Target e Campaign). Per facilitare le attività di test, è necessario configurare i webhook di Slack con un postback e caricare i file GPX nel singolo ambiente di sviluppo.

>[!IMPORTANT]
>
>Questo piano presuppone che siano stati creati dei POI nell’interfaccia utente [di gestione del servizio di](https://places.adobe.com) localizzazione e che le versioni più recenti dell’estensione Places e del monitor Luoghi siano installate e configurate correttamente.

| Passaggio | Descrizione | Risultato previsto |
|--- |--- |--- |
| 1 | Verificate che siano state immesse le chiavi manifest corrette affinché Android conceda l'accesso alla posizione di tracciamento. Per ulteriori informazioni, vedi [Aggiungere le autorizzazioni al manifesto](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confermato |
| 1a | Confermare la configurazione degli aggiornamenti della posizione in iOS. Inoltre, accertatevi di disporre delle chiavi plist appropriate in iOS per richiedere l'autorizzazione utente per tenere traccia della posizione. Per ulteriori informazioni, consultate [Attivare gli aggiornamenti di posizione in background.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confermato |
| 2 | Verificare quale modalità di monitoraggio è impostata per iOS. La modalità continua consente una maggiore precisione e persistenza, ma anche una maggiore durata della batteria. Per ulteriori informazioni, consultate Modalità [di monitoraggio (solo iOS).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Modifiche significative o continue |
| 3 | Se utilizzate più di una libreria POI, verificate che nell’estensione Luoghi per Lancio della piattaforma Experience siano state selezionate le librerie appropriate. | Confermato |
| 4 | Verificate che le versioni più recenti delle estensioni Mobile Core e Places/Places Monitor siano state incluse nell'app tramite Gradle o CocoaPods. | Confermato: per ulteriori informazioni sugli aggiornamenti recenti, consulta le note sulla [versione.](/help/release-notes.md) |
| 5 | Verificate che gli ambienti corretti siano configurati per il test. L'ID dell'ambiente Launch deve corrispondere all'ambiente di sviluppo Launch. | Confermato |
| 6 | Create file GPX per ciascun POI da verificare. I file GPX possono essere utilizzati nell'ambiente di sviluppo locale per simulare una voce di posizione. Per informazioni sulla creazione e l'utilizzo di file GPX, consultate le seguenti sezioni: File <br>[GPX per iOS Simulator [closed]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | I file GPX vengono creati e caricati nel progetto dell'app. |
| 7 | Senza fare altro, dovresti essere in grado di avviare l'applicazione da Android Studio o XCode e visualizzare l'avviso appropriato per richiedere l'accesso per il percorso di tracciamento. Fate clic sull'autorizzazione Consenti *sempre* .<br><br>È consigliabile utilizzare un dispositivo reale collegato al computer invece di utilizzare il simulatore del dispositivo. | La richiesta di posizione deve essere visualizzata nell'applicazione caricata tramite IDE |
| 8 | Una volta accettata l'autorizzazione Posizione. L’SDK Luoghi recupererà la posizione corrente del dispositivo e l’estensione Luoghi monitor inizierà a monitorare i 20 POI più vicini dalla posizione corrente | Vedere l'esempio di registro sotto la tabella. |
| 9 | La commutazione tra diverse posizioni nello studio XCode o Android dovrebbe produrre eventi di ingresso per POI specifici. Al momento dell’accesso a un POI sono previsti i seguenti registri. | Vedere l'esempio di registro sotto la tabella. |
| 10 | Dopo aver visualizzato i punti di interesse vicini nel monitor Luoghi, è necessario eseguire il test inviando i punti di interesse. In Avvia, crea una nuova regola che utilizza l'estensione Luoghi per l'attivazione in base a una voce di geotrecinto. Quindi crea una nuova azione utilizzando Mobile Core per inviare un postback. La creazione di un'app Slow Webhook consente di visualizzare voci ed uscite di posizione. Per informazioni sulla creazione di un'app Slow Webhook, vedi [Invio di messaggi tramite webhooks in arrivo.](https://api.slack.com/messaging/webhooks) |  |
| 10a | In Launch, accertati di aver aggiunto elementi di dati per l’estensione Places, tra cui: <br>Nome POI<br>corrente<br>Ultimo POI corrente<br>lungoUltimo<br>nome inseritoUltimo<br>ultimo inserito<br>lungoUltimo<br>nome uscitoUltimo<br>ultimo<br>nome uscitoUltimotimestamp |  |
| 10b | Creare una nuova regola con Evento = Luoghi → Inserisci POI |  |
| 10c | Creare un'azione = Mobile Core → Postback |  |
| 10d | Utilizzate l'URL Webhook per l'app Slack, ad esempio https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD... |  |
| 10e | Il corpo del posto sarebbe simile a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Assicurarsi di utilizzare gli elementi dati specifici creati qui. |  |
| 10f | Assicurati di pubblicare tutte le modifiche apportate ai nuovi elementi dati e alle regole in Launch. (selezionare una libreria di sviluppo funzionante in alto a destra dell'interfaccia Launch). |  |
| 11 | Avviate e verificate di nuovo l'applicazione capovolgendo le posizioni della GPX nell'IDE sviluppatore. | A questo punto, le notifiche relative alla barra laterale mostrano le voci per ciascun POI quando si selezionano diverse posizioni nell’ambiente di sviluppo. |
|  | **RAPIDO**<br>PUNTO RIEPILOGO: tutti i test possono essere condotti localmente senza dover recarsi in una posizione POI specifica. I test di convalida consentono di garantire che l'applicazione sia configurata correttamente e che abbia ricevuto le autorizzazioni corrette per il percorso. <br><br>Questa convalida garantisce inoltre che i POI definiti funzionino correttamente con l’estensione Places Monitor.  Dopo questo passaggio, inizieremo a testare i messaggi in Campaign per verificare se i messaggi corretti vengono visualizzati in base alle voci e alle uscite del POI. |  |
|  | **Verifica dei messaggi in-app standard di Adobe Campaign con il servizio di localizzazione.** |  |
| 12 | Nel dashboard principale della campagna configurate un nuovo messaggio in-app (tipo = trasmesso) |  |
| 12a | Negli attivatori, selezionare Tipo di evento **Luoghi - Immissione come attivatore**. |  |
| 12b | Selezionate **[UICONTROL Posiziona metadati]** personalizzati come filtro aggiuntivo. Utilizzate il tipo POI = Ultimo POI immesso.<br>Usiamo **[!UICONTROL Last Entered]** come tipo POI perché nella maggior parte dei casi, **[!UICONTROL Last Entered]** sarà lo stesso di **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** devono essere utilizzati solo nei casi in cui vi sono aree geografiche POI sovrapposte. In questo caso, questi POI devono essere CLASSIFICATI e quindi **[!UICONTROL Current POI]** verrà visualizzato il POI di primo livello tra le 2 o 3 aree geografiche in cui un utente potrebbe trovarsi attualmente. |  |
| 12c | Selezionate una chiave di metadati personalizzata che vi aiuterà a limitare l’ambito del POI a cui verrà inviato un messaggio. |  |
| 12d | Per la frequenza e la durata, mantenete uno o due giorni, in modo che, se non vi piacciono i criteri, possiate scadere il trigger in un periodo di tempo più breve. |  |
| 12e | Per il click-through Always/Once o Fino a, selezionate *SEMPRE* in modo da poter eseguire il test in più posizioni. | Un messaggio in-app viene visualizzato SEMPRE quando simulate una modifica di posizione che soddisfa i criteri di metadati appropriati. |
| 12f | Per la visualizzazione, selezionare un'opzione diversa da Notifica locale. Questo semplifica la visualizzazione dei test con l'app in primo piano. |  |
| 12g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 13 | Nell'ambiente di sviluppo, per assicurarsi che vengano scaricate nuove regole di campagna, chiudete e avviate nuovamente l'applicazione. | Non dimenticare che le applicazioni devono essere avviate completamente di nuovo perché il nuovo file delle regole di Campaign sia scaricato sul dispositivo. |
| 14 | Nell'applicazione di sviluppo, cambiare posizione utilizzando i file GPX creati in precedenza. | Dovresti visualizzare il messaggio in-app in base ai criteri precedenti impostati. |
| 15 | Per il test successivo, essenzialmente copieremo gli stessi passaggi di prima, ma questa volta testeremo la NOTIFICA LOCALE. | Il risultato previsto è che le notifiche locali vengono visualizzate ogni volta che vengono soddisfatti i criteri di corrispondenza. |
| 16 | Configura un nuovo messaggio in-app (tipo = trasmissione). |  |
| 16a | Nei trigger, selezionare **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16b | Selezionate i metadati Personalizzato luoghi come filtro aggiuntivo - utilizzate **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Selezionate una chiave di metadati personalizzata che vi aiuterà a limitare l’ambito del POI a cui verrà inviato un messaggio. |  |
| 16d | Per la frequenza e la durata, mantenete solo uno o due giorni, in modo che, se non vi piacciono i criteri, possiate scadere il trigger in un periodo di tempo più breve. |  |
| 16e | Per il click-through Always/Once o Fino a **[!UICONTROL ALWAYS]**. |  |
| 16f | Per il tipo di visualizzazione, selezionare **[!UICONTROL Local Notification]**. |  |
| 16g | Prepara/conferma e distribuisci il messaggio in-app. |  |
| 17 | Nell'ambiente di sviluppo, collegate il dispositivo e premete **[!UICONTROL Play]** sulla build. Dopo aver stabilito che la posizione funziona, eseguite in background l'applicazione e continuate a cambiare posizione in Xcode o Android Studio. Dovreste comunque vedere i layout della console che indicano la modifica della posizione e le notifiche locali visualizzate in base ai criteri impostati nel trigger. (potrebbe verificarsi un ritardo di 1-2 secondi). | Il risultato previsto è che le notifiche locali vengono visualizzate ogni volta che i criteri corrispondenti vengono soddisfatti. |
|  | **SINTESI PUNTO** <br>A questo punto, dovremmo vedere i POI nel nostro ambiente locale. Dovremmo inoltre visualizzare messaggi da Campaign basati sul lavoro POI. Se si verificano degli errori, controllate se una notifica di tipo Slack non è uscita. Se non è presente un messaggio di tipo Sfumatura, controllate la console dell’applicazione perché potrebbe non essere stata registrata una nuova voce di posizione. Se i risultati sono positivi, possiamo essere certi che l'applicazione funziona correttamente e che anche il servizio di messaggistica Location Service e Campaign funziona correttamente. |  |
|  | **TEST** IN SITO <br>Non è necessario modificare molto durante il test sul posto. Mantenere attivo il postback di rallentamento dovrebbe facilitare la comprensione se il dispositivo sta ottenendo una voce e un'uscita per la posizione. |  |
| 18 | Effettuare test con dispositivi che iniziano con wifi e cellulare disabilitato e quindi attivano una volta nella regione POI. | Se si verifica un errore, tenete presente se ottenete una voce di geotrecinto e una notifica in Slack. Qual è la marca temporale della notifica Slack? |
| 19 | Eseguire il test con solo cellulare abilitato e con il wifi spento. |  |
| 20 | Eseguire test con cellulare e wifi acceso. |  |
|  | **I test** on-site SUMMARY POINT <br>devono corrispondere al test di sviluppo. Tenere presente che alcuni fattori ambientali possono essere utilizzati per determinare la posizione degli utenti, come la durata del tempo trascorso in una recinzione geografica POI, la disponibilità del segnale cellulare e la forza dei punti di accesso wifi nelle vicinanze. |  |

## Esempi di registro

**** Passaggio 8: Registri iOS e Android previsti durante un aggiornamento della posizione

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**** Passaggio 9: Registri iOS e Android previsti durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
