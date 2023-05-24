---
title: Riferimento API di Places
description: Informazioni sui riferimenti API in Places.
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Riferimento API di Places {#places-api-reference}

Seguono informazioni sui riferimenti API nell’estensione Luoghi:

## Elaborazione di un evento regionale

Quando un dispositivo supera uno dei limiti predefiniti per l’area geografica dell’app, l’area geografica e il tipo di evento vengono passati all’SDK per l’elaborazione.

### ProcessGeofence (Android)

Elabora un `Geofence` evento di regione per il fornito `transitionType`.

Passa il `transitionType` da `GeofencingEvent.getGeofenceTransition()`. Attualmente `Geofence.GEOFENCE_TRANSITION_ENTER` e `Geofence.GEOFENCE_TRANSITION_EXIT` sono supportati.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Esempio**

Chiama questo metodo nel tuo `IntentService` che è registrato per la ricezione di eventi recinti geografici Android.

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

Questo metodo deve essere chiamato nel `CLLocationManager` delegate, che indica se l’utente è entrato o uscito da un’area specifica.

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

Elabora tutto `Geofences` nel `GeofencingEvent` contemporaneamente.

**Sintassi**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Esempio**

Chiama questo metodo nel tuo `IntentService` che è registrato per la ricezione di eventi recinti geografici Android

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

## Recupera i punti di interesse nelle vicinanze

Restituisce un elenco ordinato dei punti di interesse nelle vicinanze in un callback. Una versione con overload di questo metodo restituisce un codice di errore se si è verificato un errore nella chiamata di rete risultante.

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

## Recupera i punti di interesse del dispositivo corrente

Richiede un elenco di POI in cui il dispositivo è attualmente noto e lo restituisce in un callback.

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


## Ottieni la posizione del dispositivo

Richiede la posizione del dispositivo, come precedentemente noto, dall’estensione Places.

>[!TIP]
>
>L’estensione Places conosce solo le posizioni che le sono state fornite tramite chiamate a `GetNearbyPointsOfInterest`.


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

Elimina i dati lato client per l’estensione Places nello stato condiviso, nell’archiviazione locale e in memoria.

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

### cancella (iOS)

Elimina i dati lato client per l’estensione Places in stato condiviso, archiviazione locale e in memoria.

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

## Imposta stato di autorizzazione posizione

### setAuthorizationStatus (Android)

*Disponibile a partire da Places v1.4.0*

Imposta lo stato di autorizzazione nell’estensione Luoghi.

Lo stato fornito viene memorizzato nello stato condiviso Luoghi ed è solo a scopo di riferimento.
La chiamata di questo metodo non influisce sullo stato effettivo di autorizzazione della posizione per questo dispositivo.

**Sintassi**

Di seguito è riportata la sintassi per questo metodo:

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Disponibile a partire da ACPPlaces v1.3.0*

Imposta lo stato di autorizzazione nell’estensione Luoghi.

Lo stato fornito viene memorizzato nello stato condiviso Luoghi ed è solo a scopo di riferimento.
La chiamata di questo metodo non influisce sullo stato effettivo di autorizzazione della posizione per questo dispositivo.

Quando lo stato di autorizzazione del dispositivo cambia, `locationManager:didChangeAuthorizationStatus:` metodo del tuo `CLLocationManagerDelegate` viene richiamato. All’interno di questo metodo, devi trasmettere il nuovo `CLAuthorizationStatus` valore per le posizioni ACPP `setAuthorizationStatus:` API.

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
