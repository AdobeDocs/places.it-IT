---
title: Utilizzo del monitor
seo-title: Utilizzo del monitor
description: Puoi anche utilizzare i tuoi servizi di monitoraggio e integrarli con Places utilizzando le API delle estensioni Places.
seo-description: Puoi anche utilizzare i tuoi servizi di monitoraggio e integrarli con Places utilizzando le API delle estensioni Places.
translation-type: tm+mt
source-git-commit: 419df41a0abeac1ac2a77f32bfa818b4edf3baeb

---


# Utilizzo del monitor {#using-your-monitor}

Puoi anche utilizzare i tuoi servizi di monitoraggio e integrarli con Places utilizzando le API delle estensioni Places.

## Registrazione delle aree geografiche

Se decidi di utilizzare i tuoi servizi di monitoraggio, registra le aree geografiche dei punti di interesse (POI) intorno alla posizione corrente completando i seguenti passaggi:

### iOS

In iOS, completa i seguenti passaggi:

1. Passa gli aggiornamenti di posizione ottenuti dai servizi di posizione di base di iOS all'estensione Luoghi.

1. Utilizzate l'API dell'estensione `getNearbyPointsOfInterest` Places per ottenere l'array di `ACPPlacesPoi` oggetti intorno alla posizione corrente.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Estrarre le informazioni dagli `ACPPlacesPOI` oggetti ottenuti e iniziare a monitorare tali POI.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Passa gli aggiornamenti di posizione ottenuti dai servizi Google Play o Android all’estensione Places.

1. Utilizzate l'API `getNearbyPointsOfInterest` Places Extension per ottenere l'elenco di `PlacesPoi` oggetti intorno alla posizione corrente.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Estrarre i dati dagli `PlacesPOI` oggetti ottenuti e iniziare a monitorare tali POI.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


La chiamata dell' `getNearbyPointsOfInterest` API genera una chiamata di rete che ottiene la posizione intorno alla posizione corrente.

>[!IMPORTANT]
>
>È necessario chiamare l'API in modo parsimonioso o solo in caso di cambiamento significativo della posizione dell'utente.

## Registrazione di eventi geografici

### iOS

In iOS, chiama l'API `processGeofenceEvent` Places nel `CLLocationManager` delegato. Questa API vi notifica se l'utente è entrato o uscito da un'area specifica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

In Android, chiama il `processGeofence` metodo insieme all’evento di transizione appropriato nel ricevitore di trasmissione Geofence. È possibile curare l'elenco delle aree geografiche ricevute per evitare voci/uscite duplicate.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
