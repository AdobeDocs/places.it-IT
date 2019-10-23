---
title: Riferimento API Places
seo-title: Riferimento API Places
description: Informazioni sui riferimenti API in Places.
seo-description: Informazioni sui riferimenti API in Places.
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Riferimento API Places {#places-api-reference}

Informazioni sui riferimenti API in Luoghi:

## Elaborazione di un evento regione

Quando un dispositivo attraversa uno dei limiti dell'area Places predefiniti dell'app, l'area e il tipo di evento vengono passati all'SDK per l'elaborazione.

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
          // Call Adobe Places API to process information
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
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Recuperare i punti di interesse nelle vicinanze

Restituisce un elenco ordinato di POI vicini in un callback.

### GetNearbyPointsOfInterest (Android)

Di seguito è riportata la sintassi per questo metodo:

**Sintassi**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Esempio**

Di seguito è riportato un esempio di codice per questo metodo:

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNearbyPointsOfInterest (iOS)

**Sintassi**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Esempio**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
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

Richiede la posizione del dispositivo, come precedentemente noto, dall'estensione Luoghi.

>[!TIP]
>
>L'estensione Luoghi è a conoscenza solo delle posizioni che gli sono state fornite tramite chiamate a `GetNearbyPointsOfInterest`.


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
