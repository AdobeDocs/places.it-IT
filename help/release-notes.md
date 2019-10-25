---
title: Note sulla versione
seo-title: Note sulla versione
description: Note sulla versione di Adobe Experience Platform Location Service.
seo-description: Note sulla versione di Adobe Experience Platform Location Service.
translation-type: tm+mt
source-git-commit: 6ff72eb72ce3ae1abf805b7b542721a7e4915824

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione:

## 9 ottobre 2019

* **LuoghiMonitor 2.1.0**

   * **iOS**

      * È stata aggiunta una nuova API `setRequestAuthorizationLevel`per impostare il tipo di richiesta di autorizzazione di posizione per il quale verrà richiesto all'utente.
   * **Android**

      * È stata aggiunta una nuova API `setLocationPermission`per impostare il tipo di richiesta di autorizzazione di posizione per il quale verrà richiesto all'utente.
      * Il monitor Luoghi ora supporta Android 10.



## 8 agosto 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

### Aggiornamenti interfaccia

Elenco degli aggiornamenti all’interfaccia utente Luoghi:

#### Nuove funzionalità

* È stata aggiunta una nuova vista elenco in cui sono riportati i punti di interesse (POI) senza la mappa.
* Sono state aggiunte opzioni di filtro POI per la città, lo stato, il paese e i metadati.
* La prima libreria di un'organizzazione viene creata automaticamente.
* È stato aggiunto l’ordinamento POI alla vista Elenco.

#### Aggiornamenti interfaccia

* È stato spostato l’elenco e il pannello dei dettagli sul lato destro dell’interfaccia utente.
* È stato aggiunto un nuovo pannello di ricerca nella parte superiore dell’interfaccia utente.
* Se è presente una sola libreria, questa viene automaticamente selezionata quando create un POI.
* La gestione della libreria è stata spostata in una finestra a comparsa.
* È stato aggiunto un conteggio POI accanto ai filtri.

## 6 agosto 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

### Avvia monitor estensione 2.0.0

* Aggiornate le istruzioni di installazione di Android e iOS per il Monitor posizioni 2.0.

## 31 luglio 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

### Luoghi Monitor 2.0.0

* Lo stato del monitoraggio ora è persistente tra gli avvii.
* La gestione del callback, derivante da una richiesta di autorizzazione di posizione, non richiede più di estendere PlacesActivity.
* È stata modificata un'API esistente, consentendo agli sviluppatori di cancellare tutti i dati Luoghi dal dispositivo:

   API precedente: `public static void stop();`

   Nuova API: `public static void stop (final boolean clearData);`

* Aggiornamento dell'utilizzo dell' `getNearbyPointsOfInterest` API per gestire gli scenari di errore in modo più efficace.

## 25 luglio 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

### ACPPlacesMonitor 2.0.0

* Per cancellare tutti i dati Luoghi dal dispositivo,

   in ACPPlacesMonitor, sostituito un'API esistente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* Aggiornamento dell'utilizzo dell' `getNearbyPointsOfInterest` API ACPPlaces per gestire gli scenari di errore in modo più efficace.

## 22 luglio 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

### Android Places 1.3.0

* Aggiunta una nuova API che cancella tutti i dati relativi a Luoghi dallo stato condiviso, dalla memoria in-app e dalla preferenza condivisa.
* È stato risolto un problema che impediva l'aggiornamento dello stato condiviso durante l'avvio dell'applicazione.
* È stato corretto un bug a causa del quale il `getNearbyPointsOfInterest` callback restituiva il codice di errore `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` su Internet.
* `getNearbyPointsOfInterest` L'API (senza errorCallback) avrà l'elenco `successCallback` chiamato con un numero di secondi vuoto, in caso di errore nel recupero dei punti di interesse vicini.

## 19 luglio 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

**iOS Places 1.2.0**

Aggiunta una nuova API che cancella tutti i dati relativi a Luoghi dallo stato condiviso, dalla memoria in-app e `NSUserDefaults`.

## 25 giugno 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

**iOS Places Monitor 1.0.2**

* Miglioramenti della qualità della vita, compresa una migliore documentazione e registrazione dei codici.

## 17 giugno 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

**iOS Places 1.1.0**

* È stata aggiunta una nuova API per restituire un codice di errore in caso di errore nel recupero dei punti vicini.
* Quando lo stato di privacy cambia in optedout, tutti i dati relativi a Luoghi vengono cancellati dal dispositivo.
* È stato risolto un problema che, dopo un primo avvio, talvolta causava la perdita di eventi Luoghi a causa di condizioni di rete errate.
* È stato risolto un problema per il quale, durante l’elaborazione degli eventi di immissione POI in rapida successione, la sostituzione dei token tramite il modulo di gestione regole talvolta faceva riferimento a un POI non corretto.

## 30 maggio 2019 (Luoghi)

**Android Places Monitor 1.0.1**

* È stato risolto un problema che impediva un evento di immissione per i POI all’avvio del monitoraggio Luoghi.

## 28 maggio 2019

Sono stati risolti i seguenti problemi nell’interfaccia utente Luoghi:

* Aggiornato lo switcher della soluzione in Luoghi per allineare con il resto di Experience Cloud.
* È stato corretto un problema a causa del quale il livello veniva salvato nelle istanze in cui non venivano apportate modifiche al livello.
* Raggio minimo consentito nell’interfaccia utente aumentato a 10 metri.
* È stato risolto un problema per il quale, se si eliminavano tutti i numeri nel campo, il campo raggio veniva reimpostato a 20 metri.

## 17 maggio 2019 (Luoghi)

In questa versione sono stati introdotti i seguenti aggiornamenti:

**Android Places 1.1.0**

* È stata aggiunta una nuova API per l'elaborazione di un singolo oggetto Geofence.
* Correzione dei bug per evitare più eventi di immissione consecutivi.

**Android Places Monitor 1.0.0**

Rilascio iniziale del monitor Luoghi per Android.

Places Monitor gestisce le API Location a livello di sistema operativo e comunica direttamente con l'estensione Places. Con entrambe le estensioni installate, i clienti possono avere un monitoraggio out-of-the-box nella propria applicazione.
Per ulteriori informazioni sul monitor Luoghi, fate clic qui.


## 2 maggio 2019

**Android Places 1.1.0**

* È stata introdotta una nuova API per getNearByPlaces, che dispone di errorCallback e viene chiamata con un errorCode che indica il motivo dell'errore.
* L'estensione Luoghi ora mette in coda gli eventi fino a ottenere una configurazione.
* È stato aggiunto il supporto per le configurazioni basate sull'ambiente.
* Correzione bug: corrette le chiavi per gli eventi di ingresso/uscita regione
* L'archiviazione dell'ultima posizione nota ora rispetta correttamente lo stato di privacy dell'utente


## 9 aprile 2019

In questa versione sono stati introdotti i seguenti aggiornamenti:

**iOS Places Monitor 1.0.1**

* È stata aggiunta la copertura completa del test dell'unità.
* Integrazione CI (CircleCI)
* Integrazione della copertura del codice (codecov)

## 25 marzo 2019

iOS Places Monitor 1.0.0

Versione iniziale del monitor Luoghi per iOS.

Places Monitor gestisce le API Location a livello di sistema operativo e comunica direttamente con l'estensione Places. Con entrambe le estensioni installate, i clienti possono avere un monitoraggio out-of-the-box nella propria applicazione. Per ulteriori informazioni sul monitor Luoghi, consultate Estensione [Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Luoghi.

## 28 febbraio 2019

### Versione Beta

Questa è la prima release di Places, un set di strumenti che consente ai clienti di arricchire l'esperienza dei propri utenti con dati reali sulla posizione. Per la prima versione, il nostro caso d’uso principale è quello di consentire alle app mobili di recuperare dati di posizione personalizzati e di agire su tali dati tramite Adobe Experience Platform Launch.

### Funzioni chiave

Di seguito sono elencate le funzioni chiave di questa versione:

#### Interfaccia utente del servizio di localizzazione

Abbiamo rilasciato un’interfaccia utente di gestione in cui puoi visualizzare e gestire i punti di interesse (POI). Potete anche organizzare i POI in librerie. Oltre ai metadati standard come città, stato e categoria, è anche possibile aggiungere metadati personalizzati ai POI.

* Per visualizzare l’interfaccia utente, visitate [https://places.adobe.com](https://places.adobe.com).
* Per iniziare a usare l’interfaccia, consulta [Guida introduttiva](/help/getting-started.md).

#### Estensione Luoghi

Con l’estensione Luoghi potete aggiungere le vostre librerie Luoghi all’app mobile e agire sui relativi POI. Utilizzando il generatore di regole in Experience Platform Launch, puoi attivare azioni da attivare quando gli utenti entrano ed escono dai POI.

Nell'estensione Luoghi:

* Potete scegliere quali librerie POI includere nell’app.
* Eventi regola che si attivano all’entrata o all’uscita del POI.
* Crea elementi dati che puntano al POI corrente dell’utente.

Per ulteriori informazioni sull'estensione Luoghi, vedere Estensione [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

#### API Places

Puoi utilizzare le API Places per effettuare le seguenti operazioni:

* Consente agli sviluppatori di compilare e aggiornare l’elenco dei punti di interesse.
* Create una vostra interfaccia utente o integrate con un database POI esistente.
* Utilizzate gli endpoint batch API Places per effettuare un’importazione in massa di POI.

   Viene fornita un'utility python con le API.

Per ulteriori informazioni sulle API Places, vedi API [del servizio](/help/web-service-api/places-web-services.md)Web.

### Presto disponibile

#### Integrazione di Analytics

L'estensione Analytics viene aggiornata per aggiungere automaticamente i dati contestuali della posizione dal database Luoghi a tutte le chiamate Analytics in uscita quando un utente si trova all'interno di un POI (chiamate passive). Questo aggiornamento consentirà anche di creare regole per attivare le chiamate di tracciamento di Analytics direttamente alla voce POI o alla uscita (chiamate attive).

