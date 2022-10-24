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

* **Estensioni di monitor Luoghi e Luoghi**

   * Sono state aggiunte estensioni di Luoghi e Monitor Luoghi per [Reazione di applicazioni native](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Sono state aggiunte estensioni di Luoghi e Monitor Luoghi per [Applicazioni Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Per ulteriori informazioni, consulta: [Utilizzo dell’estensione Luoghi](https://docs.adobe.com/content/help/it-IT/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 maggio 2020

* **Servizio Places**

   * Importazione in blocco di POI da un file CSV utilizzando il pulsante &quot;Importa POI&quot;
   * Seleziona più POI e modifica in serie o aggiungi valori di metadati

## 6 maggio 2020

* **LuoghiMonitor 2.2.1**

   * **Android**

      * Registrazione migliorata

## 5 maggio 2020


* **LuoghiMonitor 2.1.3**

   * **iOS**

      * Registrazione migliorata

## 20 febbraio 2020

* **ACPPlaces 1.3.1 (iOS)**

   * L’estensione Luoghi ora riporta le informazioni sulla versione all’hub dell’evento nell’SDK di base.
   * Le informazioni sull’iscrizione al POI del dispositivo ora hanno un tempo di attivazione predefinito di un’ora dal momento in cui vengono raccolte. Per ulteriori informazioni, consulta [Modifica della durata dell’iscrizione a Luoghi](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Luoghi 1.4.1 (Android)**

   * L’estensione Luoghi ora riporta le informazioni sulla versione all’hub dell’evento nell’SDK di base.
   * Le informazioni sull’iscrizione al POI del dispositivo ora hanno un tempo di attivazione predefinito di un’ora dal momento in cui vengono raccolte. Per ulteriori informazioni, consulta [Modifica della durata dell’iscrizione a Luoghi](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 gennaio 2020

* **LuoghiMonitor 2.2.0**

   * **Android**

      * Chiama nuova API Places per raccogliere lo stato di autorizzazione della posizione all’avvio dell’app e quando l’autorizzazione cambia mentre l’app è in esecuzione.
      * API setRequestLocationPermission e API setLocationPermission obsolete.

## 9 gennaio 2020

* **Luoghi 1.4.0**

   * **Android**

      * È stata aggiunta una nuova API, `setAuthorizationStatus`, per impostare lo stato di autorizzazione del dispositivo per Places Services. Il valore viene memorizzato e utilizzato nello stato di condivisione Luoghi.

## 4 dicembre 2019

* **LuoghiMonitor 2.1.2**

   * **iOS**

      * Chiama l’API Luoghi per raccogliere CLAuthorizationStatus dal dispositivo quando cambia.

## 3 dicembre 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * È stata aggiunta una nuova API, `setAuthorizationStatus`, per impostare lo stato di autorizzazione del dispositivo per Places Services. Il valore viene memorizzato e utilizzato nello stato di condivisione Luoghi.

## 25 novembre 2019

* **LuoghiMonitor 2.1.1**

   * **iOS**

      * Sono state corrette le istruzioni di importazione per i progetti Cocoapods utilizzando l’opzione per più progetti pod .

## 22 novembre 2019

* **LuoghiMonitor 2.1.1**

   * **Android**

      * Il monitor ora riconosce l&#39;avvio di un dispositivo Android e, se necessario, registra nuovamente i recinti geografici con il sistema operativo in base alla posizione corrente del dispositivo.
      * È stata corretta una race condition che talvolta causava l’eliminazione degli eventi di entrata/uscita.

## 9 ottobre 2019

* **LuoghiMonitor 2.1.0**

   * **iOS**

      * È stata aggiunta una nuova API, `setRequestAuthorizationLevel`, per impostare il tipo di richiesta di autorizzazione di posizione per cui verrà richiesto all’utente.
   * **Android**

      * È stata aggiunta una nuova API, `setLocationPermission`, per impostare il tipo di richiesta di autorizzazione di posizione per cui verrà richiesto all’utente.
      * Il monitor Luoghi supporta ora Android 10.



## 8 agosto 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Aggiornamenti dell’interfaccia

Elenco degli aggiornamenti dell’interfaccia utente di Places:

#### Nuove funzionalità

* È stata aggiunta una nuova vista a elenco che mostra i punti di interesse senza la mappa.
* Sono state aggiunte opzioni di filtro POI per la città, lo stato, il paese e i metadati.
* La prima libreria di un&#39;organizzazione viene creata automaticamente.
* È stato aggiunto l’ordinamento POI nella vista a elenco.

#### Aggiornamenti dell’interfaccia

* Il pannello Elenco e dettagli è stato spostato sul lato destro dell’interfaccia utente.
* È stato aggiunto un nuovo pannello di ricerca nella parte superiore dell’interfaccia utente.
* Se è presente una sola libreria, questa viene selezionata automaticamente quando crei un POI.
* La gestione della libreria è stata spostata in una finestra a comparsa.
* È stato aggiunto un conteggio POI accanto ai filtri.

## 6 agosto 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Estensione Monitor Launch 2.0.0

* Sono state aggiornate le istruzioni di installazione di Android e iOS per Monitor Luoghi 2.0.

## 31 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Monitor Luoghi 2.0.0

* Lo stato del monitoraggio viene ora mantenuto tra un avvio e l’altro.
* La gestione del callback, derivante da una richiesta di autorizzazione di posizione, non richiede più di estendere PlacesActivity.
* È stata modificata un’API esistente, consentendo agli sviluppatori di cancellare tutti i dati di Places dal dispositivo:

   API precedente: `public static void stop();`

   Nuova API: `public static void stop (final boolean clearData);`

* È stato aggiornato l’utilizzo della `getNearbyPointsOfInterest` API per gestire gli scenari di errore in modo più efficace.

## 25 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### ACPPlacesMonitor 2.0.0

* Per cancellare tutti i dati di Luoghi dal dispositivo,

   in ACPPlacesMonitor, sostituito un&#39;API esistente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* È stato aggiornato l’uso dei moduli ACPP `getNearbyPointsOfInterest` API per gestire gli scenari di errore in modo più efficace.

## 22 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

### Posizioni Android 1.3.0

* È stata aggiunta una nuova API che cancella tutti i dati relativi a Luoghi dallo stato condiviso, dalla memoria in-app e dalla preferenza condivisa.
* È stato risolto un problema che impediva l&#39;aggiornamento dello stato condiviso durante l&#39;avvio dell&#39;applicazione.
* È stato corretto un bug in cui `getNearbyPointsOfInterest` callback: codice di errore restituito `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` su internet.
* `getNearbyPointsOfInterest` L&#39;API (senza errorCallback) avrà il `successCallback` chiamato con elenco poi vuoto, in caso di errore durante il recupero dei punti di interesse vicini.

## 19 luglio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places 1.2.0**

È stata aggiunta una nuova API che cancella tutti i dati relativi a Luoghi dallo stato condiviso, dalla memoria in-app e `NSUserDefaults`.

## 25 giugno 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places Monitor 1.0.2**

* Miglioramenti a livello di qualità della vita, inclusi documentazione e registrazione in codice migliorati.

## 17 giugno 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places 1.1.0**

* È stata aggiunta una nuova API per restituire un codice di errore in caso di errore durante il recupero di posizioni vicine.
* Quando lo stato di privacy cambia in optedout, tutti i dati relativi a Luoghi verranno cancellati dal dispositivo.
* È stato risolto un problema che, dopo un primo avvio, talvolta causava la perdita di eventi Places a causa di cattive condizioni di rete.
* È stato risolto un problema a causa del quale, durante l’elaborazione degli eventi di immissione POI in rapida successione, la sostituzione del token tramite Rules Engine talvolta fa riferimento a un POI errato.

## 30 maggio 2019

**Android Places Monitor 1.0.1**

* È stato risolto un problema che impediva un evento di immissione per POI all’avvio del monitoraggio Luoghi.

## 28 maggio 2019

Sono stati risolti i seguenti problemi nell’interfaccia utente Luoghi:

* Aggiornamento del Solution Switcher in Places per allinearlo al resto dell&#39;Experience Cloud.
* È stato risolto un problema che causava il salvataggio della classificazione nelle istanze in cui non venivano apportate modifiche di classificazione.
* Il raggio minimo consentito nell’interfaccia utente è stato aumentato a 10 metri.
* È stato risolto un problema a causa del quale, se si eliminavano tutti i numeri nel campo, il campo raggio veniva reimpostato su 20 metri.

## 17 maggio 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**Posizioni Android 1.2.0**

* È stata aggiunta una nuova API per elaborare un singolo recinto geografico.
* Correzione dei bug per evitare più eventi di immissione consecutivi.

**Android Places Monitor 1.0.0**

Versione iniziale di Monitor Luoghi per Android.

Monitor Luoghi gestisce le API di posizione a livello di sistema operativo e comunica direttamente con l’estensione Luoghi. Con entrambe le estensioni installate, i clienti possono disporre di un monitoraggio predefinito dell&#39;area nella propria applicazione.
Per ulteriori informazioni sul Monitor Luoghi, fare clic qui.


## 2 maggio 2019

**Posizioni Android 1.1.0**

* È stata introdotta una nuova API per getNearByPlaces, con un errorCallback e una chiamata con un errorCode che indica il motivo dell’errore.
* L’estensione Luoghi mette in coda gli eventi fino a quando non viene ottenuta una configurazione.
* È stato aggiunto il supporto per le configurazioni in base all’ambiente.
* Correzione bug : sono state corrette le chiavi per gli eventi di ingresso/uscita della regione
* L&#39;archiviazione dell&#39;ultima posizione nota ora rispetta correttamente lo stato di privacy dell&#39;utente


## 9 aprile 2019

In questa versione sono stati apportati i seguenti aggiornamenti:

**iOS Places Monitor 1.0.1**

* È stata aggiunta la copertura completa del test di unità.
* Integrazione CI (CircleCI)
* Integrazione della copertura del codice (codecov)

## 25 marzo 2019

iOS Places Monitor 1.0.0

Versione iniziale di Monitor Luoghi per iOS.

Monitor Luoghi gestisce le API di posizione a livello di sistema operativo e comunica direttamente con l’estensione Luoghi. Con entrambe le estensioni installate, i clienti possono disporre di un monitoraggio predefinito dell&#39;area nella propria applicazione.

## 28 febbraio 2019

### Versione beta

Questa è la prima versione di Places Service, un set di strumenti che consente ai clienti di arricchire le esperienze dei propri utenti con i dati sulla posizione reale. Per la prima versione, il nostro caso d’uso principale è quello di consentire alle app mobili di recuperare dati di posizione personalizzati e di agire su tali dati tramite Adobe Experience Platform Launch.

### Funzioni chiave

Di seguito sono elencate le funzioni chiave di questa versione:

#### Interfaccia utente di Places Service

È stata rilasciata un’interfaccia utente di gestione per la visualizzazione e la gestione dei punti di interesse (POI). Puoi anche organizzare i punti di interesse in librerie. Oltre ai metadati standard come città, stato e categoria, è supportata anche la possibilità di aggiungere metadati personalizzati ai punti di interesse.

* Per visualizzare l’interfaccia utente, passa a [https://places.adobe.com](https://places.adobe.com).
* Per iniziare a utilizzare l’interfaccia utente, vedi [Introduzione](/help/getting-started.md).

#### Estensione Luoghi

Utilizzando l’estensione Places, puoi aggiungere le librerie di Places Service all’app mobile e intervenire sui relativi POI. Utilizzando il generatore di regole in Experience Platform Launch, puoi attivare le azioni quando gli utenti entrano ed escono dai punti di interesse.

Nell’estensione Luoghi:

* Puoi scegliere quali librerie POI includere nell’app.
* Eventi di regole che si attivano all’ingresso o all’uscita del POI.
* Crea elementi dati che puntano al POI corrente dell&#39;utente.

Per ulteriori informazioni sull’estensione Luoghi, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API di Luoghi

Puoi utilizzare le API di Places per effettuare le seguenti operazioni:

* Consenti agli sviluppatori di compilare e aggiornare l’elenco dei punti di interesse.
* Crea la tua interfaccia utente o integra con un database POI esistente.
* Utilizza gli endpoint batch API Places per effettuare un’importazione in massa di POI.

   È possibile utilizzare l&#39;utilità Python fornita per completare l&#39;importazione in serie.

Per ulteriori informazioni sulle API di Places, consulta [API del servizio Web](/help/web-service-api/places-web-services.md).

### Disponibile a breve

#### Integrazione di Analytics

L’estensione Analytics viene aggiornata per aggiungere automaticamente i dati contestuali della posizione dal database di Places Service a tutte le chiamate Analytics in uscita quando un utente si trova in un POI (chiamate passive). Questo aggiornamento consentirà anche la creazione di regole per attivare le chiamate di tracciamento di Analytics direttamente all’entrata o all’uscita POI (chiamate attive).
