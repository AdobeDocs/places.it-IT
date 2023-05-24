---
title: Note sulla versione
description: Note sulla versione di Places Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# Note sulla versione {#release-notes}

## 8 luglio 2020

* **Estensioni del monitoraggio di Places e Places**

   * Sono state aggiunte le estensioni Monitor luoghi e luoghi per [React - Applicazioni native](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Sono state aggiunte le estensioni Monitor luoghi e luoghi per [Applicazioni Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Per ulteriori informazioni, consulta: [Utilizzo dell’estensione Places](https://docs.adobe.com/content/help/it-IT/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 maggio 2020

* **Servizio Places**

   * Importare in blocco i POI da un file CSV utilizzando il pulsante &quot;Import POIs&quot; (Importa POI)
   * Seleziona più punti di interesse e modifica in blocco o aggiungi valori di metadati

## 6 maggio 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Registrazione migliorata

## 5 maggio 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Registrazione migliorata

## 20 febbraio 2020

* **ACPPlaces 1.3.1 (iOS)**

   * L’estensione Places ora segnala le informazioni sulla versione all’hub eventi nell’SDK core.
   * Ora le informazioni sull’iscrizione al punto di interesse del dispositivo hanno un time-to-live predefinito di un’ora dal momento in cui vengono raccolte. Per ulteriori informazioni, consulta [Modifica del time-to-live dell’iscrizione a Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * L’estensione Places ora segnala le informazioni sulla versione all’hub eventi nell’SDK core.
   * Ora le informazioni sull’iscrizione al punto di interesse del dispositivo hanno un time-to-live predefinito di un’ora dal momento in cui vengono raccolte. Per ulteriori informazioni, consulta [Modifica del time-to-live dell’iscrizione a Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 gennaio 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Chiama la nuova API Luoghi per raccogliere lo stato di autorizzazione della posizione quando l’app viene avviata e quando l’autorizzazione cambia mentre l’app è in esecuzione.
      * Sono state aggiunte le API setRequestLocationPermission e setLocationPermission obsolete.

## 9 gennaio 2020

* **Places 1.4.0**

   * **Android**

      * È stata aggiunta una nuova API, `setAuthorizationStatus`, per impostare lo stato di autorizzazione del dispositivo per Places Services. Il valore viene memorizzato e utilizzato nello stato condiviso Luoghi.

## 4 dicembre 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Chiama l’API Places per raccogliere CLAAuthorizationStatus dal dispositivo quando viene modificato.

## 3 dicembre 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * È stata aggiunta una nuova API, `setAuthorizationStatus`, per impostare lo stato di autorizzazione del dispositivo per Places Services. Il valore viene memorizzato e utilizzato nello stato condiviso Luoghi.

## 25 novembre 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Sono state corrette le istruzioni di importazione per i progetti Cocoapods utilizzando l’opzione Più progetti pod.

## 22 novembre 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * Il monitor ora riconosce l&#39;avvio di un dispositivo Android e, se necessario, registra nuovamente i recinti geografici con il sistema operativo in base alla posizione corrente del dispositivo.
      * È stata risolta una situazione di tipo &quot;race condition&quot; a causa della quale a volte gli eventi di entrata/uscita venivano eliminati.

## 9 ottobre 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * È stata aggiunta una nuova API, `setRequestAuthorizationLevel`, per impostare il tipo di richiesta di autorizzazione per la posizione per la quale verrà richiesto all&#39;utente.
   * **Android**

      * È stata aggiunta una nuova API, `setLocationPermission`, per impostare il tipo di richiesta di autorizzazione per la posizione per la quale verrà richiesto all&#39;utente.
      * Il Monitor Luoghi ora supporta Android 10.



## 8 agosto 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Aggiornamenti dell’interfaccia utente

Elenco degli aggiornamenti all’interfaccia utente Luoghi:

#### Nuove funzionalità

* È stata aggiunta una nuova vista a elenco che mostra i punti di interesse senza la mappa.
* Sono state aggiunte opzioni di filtro POI per la città, lo stato, il paese e i metadati.
* La prima libreria di un’organizzazione viene creata automaticamente.
* È stato aggiunto l’ordinamento dei punti di interesse alla vista a elenco.

#### Aggiornamenti dell’interfaccia utente

* L’elenco e il pannello dei dettagli sono stati spostati sul lato destro dell’interfaccia utente.
* È stato aggiunto un nuovo pannello di ricerca nella parte superiore dell’interfaccia utente.
* Se è presente una sola libreria, questa viene selezionata automaticamente al momento della creazione di un POI.
* La gestione della libreria è stata spostata in una finestra a comparsa.
* È stato aggiunto un conteggio POI accanto ai filtri.

## 6 agosto 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Estensione Monitor Launch 2.0.0

* Sono state aggiornate le istruzioni di installazione di Android e iOS per Places Monitor 2.0.

## 31 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Monitor Luoghi 2.0.0

* Lo stato del monitoraggio ora viene mantenuto tra i lanci.
* La gestione del callback, derivante da una richiesta di autorizzazione della posizione, non richiede più l’estensione di PlacesActivity.
* È stata modificata un’API esistente che consente agli sviluppatori di cancellare tutti i dati di Places dal dispositivo:

   Vecchia API: `public static void stop();`

   Nuova API: `public static void stop (final boolean clearData);`

* È stato aggiornato l’utilizzo di `getNearbyPointsOfInterest` API per gestire gli scenari di errore in modo più efficace.

## 25 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### ACPPlacesMonitor 2.0.0

* Per cancellare tutti i dati Places dal dispositivo:

   in ACPPlacesMonitor, ha sostituito un’API esistente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* È stato aggiornato l’utilizzo di ACPPlaces `getNearbyPointsOfInterest` API per gestire gli scenari di errore in modo più efficace.

## 22 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Android Places 1.3.0

* È stata aggiunta una nuova API che cancella tutti i dati relativi a Places da stato condiviso, memoria in-app e preferenza condivisa.
* È stato risolto un problema che impediva l&#39;aggiornamento dello stato condiviso durante l&#39;avvio dell&#39;applicazione.
* È stato corretto un bug in cui `getNearbyPointsOfInterest` il callback restituiva un codice di errore `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` su internet.
* `getNearbyPointsOfInterest` API (senza errorCallback) avrà il `successCallback` chiamato con elenco poi vuoto, in caso di errore durante il recupero dei punti di interesse vicini.

## 19 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places 1.2.0**

È stata aggiunta una nuova API che cancella tutti i dati relativi a Places dallo stato condiviso, dalla memoria in-app e `NSUserDefaults`.

## 25 giugno 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places Monitor 1.0.2**

* Miglioramenti nella qualità della vita, inclusa una migliore documentazione nel codice e registrazione.

## 17 giugno 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places 1.1.0**

* È stata aggiunta una nuova API per restituire un codice di errore in caso di errore durante il recupero di luoghi vicini.
* Quando lo stato di privacy cambia in optedout, tutti i dati relativi a Places verranno cancellati dal dispositivo.
* È stato risolto un problema che, dopo un primo avvio, a volte causava la perdita di eventi Places a causa di condizioni di rete non corrette.
* È stato risolto un problema a causa del quale, durante l’elaborazione degli eventi di immissione dei POI in rapida successione, la sostituzione dei token tramite Rules Engine (Motore di regole) talvolta faceva riferimento al POI errato.

## 30 maggio 2019

**Android Places Monitor 1.0.1**

* È stato risolto un problema che impediva un evento di ingresso per i punti di interesse all’avvio del monitoraggio di Places.

## 28 maggio 2019

Sono stati risolti i seguenti problemi nell’interfaccia utente Luoghi:

* Lo switcher della soluzione in Places è stato aggiornato per allinearlo al resto dell’Experience Cloud.
* È stato risolto un problema che causava il salvataggio della classificazione nelle istanze in cui non venivano apportate modifiche alla classificazione.
* Il raggio minimo consentito nell’interfaccia utente è stato aumentato a 10 metri.
* È stato risolto un problema a causa del quale, se si eliminavano tutti i numeri nel campo, il campo del raggio veniva ripristinato a 20 metri.

## 17 maggio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**Android Places 1.2.0**

* È stata aggiunta una nuova API per elaborare un singolo recinto geografico.
* Correzione di bug per evitare più eventi di ingresso consecutivi.

**Android Places Monitor 1.0.0**

Versione iniziale di Places Monitor per Android.

Places Monitor gestisce le API di posizione a livello di sistema operativo e comunica direttamente con l’estensione Places. Con entrambe le estensioni installate, i clienti possono avere un monitoraggio predefinito per l’area geografica nella loro applicazione.
Per ulteriori informazioni sul monitor Luoghi, fare clic qui.


## 2 maggio 2019

**Android Places 1.1.0**

* È stata introdotta una nuova API per getNearByPlaces, che presenta un errorCallback e viene chiamata con un errorCode che indica il motivo dell’errore.
* L’estensione Places ora mette in coda gli eventi fino a quando non viene ottenuta una configurazione.
* È stato aggiunto il supporto per le configurazioni in base all’ambiente.
* Correzione bug : sono state corrette le chiavi per gli eventi di entrata/uscita di regione
* L’archiviazione dell’ultima posizione conosciuta ora rispetta correttamente lo stato di privacy dell’utente


## 9 aprile 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places Monitor 1.0.1**

* È stata aggiunta la copertura completa dello unit test.
* Integrazione CI (CircleCI)
* Integrazione code coverage (codecov)

## 25 marzo 2019

iOS Places Monitor 1.0.0

Versione iniziale di Places Monitor per iOS.

Places Monitor gestisce le API di posizione a livello di sistema operativo e comunica direttamente con l’estensione Places. Con entrambe le estensioni installate, i clienti possono avere un monitoraggio predefinito per l’area geografica nella loro applicazione.

## 28 febbraio 2019

### Versione beta

Questa è la prima versione di Places Service, un insieme di strumenti che consente ai clienti di arricchire le esperienze degli utenti con dati reali sulla posizione. Per la prima versione, il nostro caso d’uso principale è quello di consentire alle app mobili di recuperare dati di posizione personalizzati e agire su di essi tramite Adobe Experience Platform Launch.

### Funzioni chiave

Di seguito sono riportate le funzioni chiave di questa versione:

#### Interfaccia utente di Places Service

È stata rilasciata un’interfaccia utente di gestione che consente di visualizzare e gestire i punti di interesse (POI). Puoi anche organizzare i punti di interesse in librerie. Oltre ai metadati standard come città, stato e categoria, è supportata anche la possibilità di aggiungere metadati personalizzati ai punti di interesse.

* Per visualizzare l’interfaccia utente, vai a [https://places.adobe.com](https://places.adobe.com).
* Per iniziare a utilizzare l’interfaccia utente, consulta [Introduzione](/help/getting-started.md).

#### Estensione Luoghi

Utilizzando l’estensione Places, puoi aggiungere le librerie del servizio Places alla tua app mobile e agire in base ai loro POI. Utilizzando il generatore di regole in Experience Platform Launch, puoi attivare azioni quando gli utenti entrano ed escono dai POI.

Nell’estensione Luoghi:

* Puoi scegliere quali librerie POI includere nell&#39;app.
* Eventi di regola che si attivano all’entrata o all’uscita da un POI.
* Crea elementi di dati che puntano al POI corrente dell’utente.

Per ulteriori informazioni sull’estensione Luoghi, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API Places

Puoi utilizzare le API Places per effettuare le seguenti operazioni:

* Consenti agli sviluppatori di compilare e aggiornare l’elenco dei POI.
* Crea una tua interfaccia utente o integra con un database POI esistente.
* Utilizza gli endpoint batch dell’API Luoghi per effettuare un’importazione in blocco di POI.

   È possibile utilizzare l&#39;utilità Python fornita per completare l&#39;importazione in blocco.

Per ulteriori informazioni sulle API Places, consulta [API servizio web](/help/web-service-api/places-web-services.md).

### In arrivo

#### Integrazione di Analytics

L’estensione Analytics viene aggiornata per aggiungere automaticamente i dati contestuali sulla posizione dal database Places Service a tutte le chiamate Analytics in uscita quando un utente si trova in un POI (chiamate passive). Questo aggiornamento consente inoltre di creare regole per attivare il tracciamento delle chiamate di Analytics direttamente all’entrata o all’uscita dal POI (chiamate attive).
