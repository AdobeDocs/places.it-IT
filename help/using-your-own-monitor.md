---
title: Utilizzo del proprio monitor
description: Puoi anche utilizzare i servizi di monitoraggio e integrarli con Places Service utilizzando le API dell’estensione Places Service.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Utilizzo del proprio monitor {#using-your-monitor}

Puoi anche utilizzare i servizi di monitoraggio e integrarli con Places Service utilizzando le API dell’estensione Places.

## Registrazione dei recinti geografici

Se decidi di utilizzare i servizi di monitoraggio, registra i recinti geografici dei POI intorno alla posizione corrente completando i passaggi seguenti:

### iOS

In iOS, completa i seguenti passaggi:

1. Passa all’estensione Places gli aggiornamenti sulla posizione ottenuti dai servizi di posizione core di iOS.

1. Utilizza il `getNearbyPointsOfInterest` API dell’estensione Places per ottenere l’array di `ACPPlacesPoi` intorno alla posizione corrente.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Estrarre le informazioni dal ottenuto `ACPPlacesPOI` e iniziare a monitorarli.

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

1. Passa all’estensione Places gli aggiornamenti sulla posizione ottenuti dai servizi Google Play o dai servizi di posizione Android.

1. Utilizza il `getNearbyPointsOfInterest` API di estensione Places per ottenere l’elenco di `PlacesPoi` intorno alla posizione corrente.

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

1. Estrai i dati dal ottenuto `PlacesPOI` e iniziare a monitorarli.

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


Chiamata di `getNearbyPointsOfInterest` L’API genera una chiamata di rete che ottiene la posizione intorno alla posizione corrente.

>[!IMPORTANT]
>
>È necessario chiamare l’API con moderazione o solo quando si verifica un cambiamento significativo della posizione dell’utente.

## Registrazione di eventi recinto geografico

### iOS

In iOS, chiama il `processGeofenceEvent` Posiziona l’API in `CLLocationManager` delegato. Questa API indica se l’utente ha iniziato o chiuso l’accesso a un’area specifica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

In Android, chiama il `processGeofence` insieme all’evento di transizione appropriato nel ricevitore di trasmissione Geofence. Puoi curare l’elenco dei recinti geografici ricevuti per evitare duplicati di entrate/uscite.

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
