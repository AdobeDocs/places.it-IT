---
title: Riferimento API di Monitoraggio luoghi
seo-title: Riferimento API di Monitoraggio luoghi
description: 'Un elenco delle API per il Monitor posizioni. '
seo-description: 'Un elenco delle API per il Monitor posizioni.  '
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Riferimento API di Monitoraggio luoghi {#places-api-reference}

## Registra estensione monitor luoghi

Registra l’estensione Places Monitor con l’hub eventi di base.

### RegisterExtension (Android)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

Di seguito è riportata la sintassi in Java:

```java
public static void registerExtension();
```

#### Esempio

Chiama questo metodo nel `onCreate` metodo in cui inizializza il resto dell’SDK della piattaforma Experience.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

Di seguito è riportata la sintassi in Objective-C:

```objective-c
+ (void) registerExtension;
```

#### Esempio

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Versione estensione

Restituisce la versione corrente dell'estensione Places Monitor

### ExtensionVersion (Android)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static String extensionVersion();
```

#### Esempio

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Esempio

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Avvia monitoraggio dispositivo

Iniziare a monitorare la posizione del dispositivo e i luoghi vicini.

### Start (Android)

Se l'autorizzazione per utilizzare la posizione del dispositivo non è stata concessa dall'utente, la prima chiamata all' `start` API richiede all'utente l'autorizzazione.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static void start();
```

#### Esempio

```java
PlacesMonitor.start();
```

### Start (iOS)

>[!IMPORTANT]
>
>Per iniziare il monitoraggio, il servizio di localizzazione deve disporre dell'autorizzazione necessaria:
>
>* Se l'autorizzazione per il servizio di posizione non è stata fornita all'applicazione, la prima chiamata all' `start` API richiede l'autorizzazione per utilizzare il servizio di posizione come configurato per l'applicazione.
>* A seconda delle capacità del dispositivo, se l'autorizzazione è stata fornita, il monitor Luoghi tiene traccia della posizione dell'utente in base al set attualmente `ACPPlacesMonitorMode`. Per impostazione predefinita, il monitor utilizza `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Se la chiamata per avviare il monitoraggio viene effettuata prima che l’SDK abbia terminato l’inizializzazione, potrebbe essere ignorata.

Puoi verificare che l’SDK abbia terminato l’inizializzazione chiamando `start` dal callback fornito a `ACPCore::start:`.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objectivec
+ (void) start;
```

#### Esempio

Avvio di Monitoraggio luoghi durante l'inizializzazione dell'SDK:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Avvio di Monitoraggio luoghi più tardi nell'esecuzione dell'app:

```objective-c
[ACPPlacesMonitor start];
```

## Arresta monitoraggio dispositivo

Interrompe il tracciamento della posizione del dispositivo.

### Interrompi (Android)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static void stop();
```

#### Esempio

```java
PlacesMonitor.stop();
```

### Interrompi (iOS)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objectivec
+ (void) stop;
```

#### Esempio

```objective-c
[ACPPlacesMonitor stop];
```

## Aggiorna posizione

Utilizzate questa API per un aggiornamento immediato sulla posizione del dispositivo. Quando chiamate questa API, il dispositivo tenta di determinare la posizione con il livello di precisione specificato. Questo processo aggiorna anche i POI vicini monitorati dall’estensione.

### UpdateLocation (Android)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static void updateLocation();
```

#### Esempio

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Sintassi

```objective-c
+ (void) updateLocationNow;
```

#### Esempio

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Autorizzazione Posizione app

Potete utilizzare questa API per impostare il tipo di autorizzazione di posizione che l'utente riceve e che è autorizzato a utilizzare per i servizi di posizione.

### SetLocationPermission (Android)

Questa API imposta il tipo di richiesta di autorizzazione di posizione per il quale l'utente deve essere selezionato.

>[!TIP]
>
>Questa API è valida solo per i dispositivi che si trovano su Android 10 e versioni successive.
>
>Per impostare la richiesta di autorizzazione appropriata da visualizzare all'utente, chiama questa API prima dell' `PlacesMonitor.start()`. La chiamata di questo metodo, durante il monitoraggio attivo, aggiorna il livello di autorizzazione della posizione al valore di autorizzazione richiesto. Se il livello di autorizzazione richiesto è già fornito o rifiutato dall'utente dell'applicazione, o se tentate di eseguire il downgrade dell'autorizzazione da `ALWAYS_ALLOW` `WHILE_USING_APP`a, questo metodo non ha alcun effetto.

L’autorizzazione posizione può essere impostata su uno dei seguenti valori:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Questo valore richiede all'utente di accedere alla posizione del dispositivo solo quando utilizza l'applicazione. Un'app è considerata in uso quando l'utente sta visualizzando l'app sullo schermo del proprio dispositivo, ad esempio un'attività è in esecuzione in primo piano.

   >[!TIP]
   >
   >Accertatevi che l'autorizzazione utente ACCESS_FINE_LOCATION sia impostata nel file manifesto dell'app.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Questo valore richiede all'utente di accedere alla posizione del dispositivo anche quando l'applicazione viene messa in background.

   >[!TIP]
   >
   >Assicurati che le autorizzazioni utente ACCESS_BACKGROUND_LOCATION e ACCESS_FINE_LOCATION siano impostate nel file manifesto dell'app.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` è il valore di autorizzazione di posizione predefinito.

>[!IMPORTANT]
>
>Se all'utente dell'app viene concessa l' `WHILE_USING_APP` autorizzazione, le aree geografiche non verranno registrate nel sistema operativo. Di conseguenza, l’estensione Luoghi monitor non attiva eventi di ingresso/uscita sulle aree che si stanno verificando in background.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Esempio

Per richiedere l' `WHILE_USING_APP` autorizzazione:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Per effettuare l'aggiornamento all' `ALWAYS_ALLOW` autorizzazione:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Questa API imposta il tipo di richiesta di autorizzazione di posizione per il quale verrà richiesto all'utente.

Per impostare la richiesta di autorizzazione appropriata da visualizzare all'utente, chiamate `SetRequestAuthorizationLevel` prima di chiamare `[ACPPlacesMonitor start]`. Per impostare il prompt di autorizzazione appropriato da mostrare all'utente, chiamate questa API prima del `[ACPPlacesMonitor start]`. Se si richiama questo metodo durante il monitoraggio attivo, il livello di autorizzazione della posizione verrà aggiornato al valore di autorizzazione richiesto. Se il livello di autorizzazione richiesto è già fornito o rifiutato dall'utente dell'applicazione o se esiste un downgrade dell'autorizzazione da `ACPPlacesRequestAuthorizationLevelAlways` a `ACPPlacesRequestAuthorizationLevelWhenInUse` autorizzazione, questo metodo non ha effetto.

Il livello di autorizzazione può essere impostato su uno dei seguenti valori:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Richiede l'autorizzazione dell'utente per utilizzare i servizi di posizione mentre l'app è in uso. Il prompt dell'utente contiene il testo della `NSLocationWhenInUseUsageDescription` chiave nel file info.plist dell'app, e la presenza di tale chiave è necessaria quando si chiama questo metodo. Per ulteriori informazioni, consulta la documentazione [Apple su requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Utilizzate questo enum per richiedere servizi di localizzazione anche quando l'app è in background. Devi avere le chiavi `NSLocationAlwaysUsageDescription` e nella `NSLocationWhenInUseUsageDescription` lista Info.plist dell'app. Queste chiavi definiscono il testo che verrà visualizzato durante il prompt dell'utente. Per ulteriori informazioni, consultate la documentazione [Apple su requestalwayspermissions](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` è il valore predefinito di autorizzazione della richiesta.

>[!IMPORTANT]
>
>L'applicazione che ha autorizzato l'uso dell' `ACPPlacesRequestAuthorizationLevelWhenInUse` autorizzazione non sarà in grado di attivare eventi di ingresso/uscita sulle aree che si stanno verificando in background.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel
```

#### Esempio

Per richiedere l' `ACPPlacesRequestAuthorizationLevelWhenInUse` autorizzazione:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Per eseguire l'aggiornamento all' `ACPPlacesRequestAuthorizationLevelAlways` autorizzazione:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways]
```

## Modalità di monitoraggio (solo iOS)

Il monitoraggio può essere impostato su uno dei seguenti valori:

* `ACPPlacesMonitorModeContinuous`

   L'estensione di monitoraggio riceve ed elabora le posizioni più frequentemente. Questa strategia di monitoraggio consuma molta energia ma fornisce una maggiore precisione. Per ulteriori informazioni, consulta la documentazione [Apple sul monitoraggio](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)continuo.

* `ACPPlacesMonitorModeSignificantChanges`

   L'estensione di monitoraggio riceve ed elabora gli aggiornamenti della posizione solo dopo che il dispositivo si è spostato a una distanza significativa dalla posizione precedentemente elaborata. Questa strategia di monitoraggio consuma meno energia rispetto alla strategia di monitoraggio continuo. Per ulteriori informazioni, consulta la documentazione [Apple sul monitoraggio significativo](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Esempio

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
