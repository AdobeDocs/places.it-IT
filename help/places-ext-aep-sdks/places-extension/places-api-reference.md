---
title: Riferimento API Places
description: Informazioni sui riferimenti API in Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Riferimento API Places {#places-api-reference}

Informazioni sui riferimenti API in Luoghi:

## Elaborazione di un evento regione

Quando un dispositivo attraversa uno dei limiti dell&#39;area Places predefiniti dell&#39;app, l&#39;area e il tipo di evento vengono passati all&#39;SDK per l&#39;elaborazione.

### ProcessGeofence (Android)

Elabora un evento `Geofence` regione per il provider `transitionType`.

Passa la `transitionType` da `GeofencingEvent.getGeofenceTransition()`. Attualmente `Geofence.GEOFENCE_TRANSITION_ENTER` e `Geofence.GEOFENCE_TRANSITION_EXIT` sono supportati.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Esempio**

Chiama questo metodo nel tuo account `IntentService` registrato per ricevere eventi di geofence Android.

Di seguito è riportato un esempio di codice per questo metodo:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Questo metodo deve essere chiamato nel `CLLocationManager` delegato, che indica se l’utente è entrato o uscito da una regione specifica.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

Elabora tutti `Geofences` allo `GeofencingEvent` stesso tempo.

**Sintassi**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Esempio**

Chiama questo metodo nel tuo `IntentService` che è registrato per ricevere eventi di geofence Android

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Recuperare i punti di interesse nelle vicinanze

Restituisce un elenco ordinato di POI vicini in un callback. Una versione sovraccaricata di questo metodo restituisce un codice di errore se si è verificato un errore con la chiamata di rete risultante.

### GetNearbyPointsOfInterest (Android)

Di seguito è riportata la sintassi per questo metodo:

**Sintassi**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNearbyPointsOfInterest (iOS)

**Sintassi**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Esempio**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Recupera punti di interesse dispositivo correnti

Richiede un elenco di POI in cui è attualmente noto che il dispositivo si trova e li restituisce in una callback.

### GetCurrentPointsOfInterest (Android)

Di seguito è riportata la sintassi per questo metodo:

**Sintassi**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Ottenere la posizione del dispositivo

Richiede la posizione del dispositivo, come precedentemente noto, dall&#39;estensione Luoghi.

>[!TIP]
>
>L&#39;estensione Luoghi è a conoscenza solo delle posizioni che gli sono state fornite tramite chiamate a `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Cancella dati lato client


### Cancella (Android)

Elimina i dati lato client per i Luoghi in stato condiviso, archiviazione locale e memoria.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```java
public static void clear();
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
Places.clear();
```

### clear (iOS)

Elimina i dati lato client per i Luoghi in stato condiviso, archiviazione locale e memoria.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```objectivec
+ (void) clear;
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```objectivec
[ACPPlaces clear];
```

## Imposta stato autorizzazione posizione

### setAuthorizationStatus (Android)

Disponibile a breve

### setAuthorizationStatus (iOS)

*Disponibile a partire da ACPPlaces v1.3.0*

Imposta lo stato dell&#39;autorizzazione nell&#39;estensione Luoghi.

Lo stato fornito è memorizzato nello stato Condiviso Luoghi e lo è solo per riferimento.
La chiamata di questo metodo non influisce sullo stato effettivo dell&#39;autorizzazione di posizione per il dispositivo.

Quando lo stato dell&#39;autorizzazione del dispositivo cambia, viene richiamato il `locationManager:didChangeAuthorizationStatus:` metodo del `CLLocationManagerDelegate` dispositivo. Dall&#39;interno di questo metodo, è necessario trasmettere il nuovo `CLAuthorizationStatus` valore all&#39; `setAuthorizationStatus:` API ACPPlaces.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
