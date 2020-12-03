---
title: Riferimento API di Monitoraggio luoghi
description: Un elenco delle API per il Monitor posizioni.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 2%

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

Chiama questo metodo nel `onCreate` metodo in cui inizializza il resto dell’SDK del Experience Platform .

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

Restituisce la versione corrente dell&#39;estensione Places Monitor

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

Se l&#39;autorizzazione per utilizzare la posizione del dispositivo non è stata concessa dall&#39;utente, la prima chiamata all&#39; `start` API richiede all&#39;utente l&#39;autorizzazione.

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
>Per iniziare il monitoraggio, il servizio di localizzazione deve disporre dell&#39;autorizzazione necessaria:
>
>* Se l&#39;autorizzazione per il servizio Places non è stata fornita all&#39;applicazione, la prima chiamata all&#39; `start` API richiede l&#39;autorizzazione per utilizzare il servizio Places come configurato per l&#39;applicazione.
>* A seconda delle capacità del dispositivo, se l&#39;autorizzazione è stata fornita, il monitor Luoghi tiene traccia della posizione dell&#39;utente in base al set attualmente `ACPPlacesMonitorMode`. Per impostazione predefinita, il monitor utilizza `ACPPlacesMonitorModeSignificantChanges`.


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

Avvio di Monitoraggio luoghi durante l&#39;inizializzazione dell&#39;SDK:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Avvio di Monitoraggio luoghi più tardi nell&#39;esecuzione dell&#39;app:

```objective-c
[ACPPlacesMonitor start];
```

## Arresta il monitoraggio del dispositivo

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

Utilizzate questa API per un aggiornamento immediato sulla posizione del dispositivo. Quando si chiama questa API, il dispositivo tenta di determinare la posizione con il livello di precisione specificato. Questo processo aggiorna anche i POI vicini monitorati dall’estensione.

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

Potete utilizzare questa API per impostare il tipo di autorizzazione di posizione che l&#39;utente riceve e che l&#39;utente è autorizzato a utilizzare per il servizio Places.

### SetLocationPermission (Android)

Questa API imposta il tipo di richiesta di autorizzazione di posizione per il quale l&#39;utente deve essere selezionato.

>[!TIP]
>
>Questa API è valida solo per i dispositivi che si trovano su Android 10 e versioni successive.
>
>Per impostare la richiesta di autorizzazione appropriata da visualizzare all&#39;utente, chiama questa API prima dell&#39; `PlacesMonitor.start()`. La chiamata di questo metodo, durante il monitoraggio attivo, aggiorna il livello di autorizzazione della posizione al valore di autorizzazione richiesto. Se il livello di autorizzazione richiesto è già fornito o rifiutato dall&#39;utente dell&#39;applicazione, o se tentate di eseguire il downgrade dell&#39;autorizzazione da `ALWAYS_ALLOW` `WHILE_USING_APP`a, questo metodo non ha alcun effetto.

L’autorizzazione posizione può essere impostata su uno dei seguenti valori:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Questo valore richiede all&#39;utente di accedere alla posizione del dispositivo solo quando utilizza l&#39;applicazione. Un&#39;app è considerata in uso quando l&#39;utente sta visualizzando l&#39;app sullo schermo del proprio dispositivo, ad esempio un&#39;attività è in esecuzione in primo piano.

   >[!TIP]
   >
   >Accertatevi che l&#39;autorizzazione utente ACCESS_FINE_LOCATION sia impostata nel file manifesto dell&#39;app.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Questo valore richiede all&#39;utente di accedere alla posizione del dispositivo anche quando l&#39;applicazione viene messa in background.

   >[!TIP]
   >
   >Assicurati che le autorizzazioni utente ACCESS_BACKGROUND_LOCATION e ACCESS_FINE_LOCATION siano impostate nel file manifesto dell&#39;app.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` è il valore di autorizzazione di posizione predefinito.

>[!IMPORTANT]
>
>Se all&#39;utente dell&#39;app viene concessa l&#39; `WHILE_USING_APP` autorizzazione, le aree geografiche non verranno registrate nel sistema operativo. Di conseguenza, l’estensione Luoghi monitor non attiva eventi di ingresso/uscita sulle aree che si stanno verificando in background.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Esempio

Per richiedere l&#39; `WHILE_USING_APP` autorizzazione:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Per effettuare l&#39;aggiornamento all&#39; `ALWAYS_ALLOW` autorizzazione:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Questa API imposta il tipo di richiesta di autorizzazione di posizione per il quale verrà richiesto all&#39;utente.

Per impostare il prompt di autorizzazione appropriato da visualizzare all&#39;utente, chiamate `SetRequestAuthorizationLevel` prima di chiamare `[ACPPlacesMonitor start]`. Per impostare il prompt di autorizzazione appropriato da mostrare all&#39;utente, chiamate questa API prima del `[ACPPlacesMonitor start]`. Se si richiama questo metodo durante il monitoraggio attivo, il livello di autorizzazione della posizione verrà aggiornato al valore di autorizzazione richiesto. Se il livello di autorizzazione richiesto è già fornito o rifiutato dall&#39;utente dell&#39;applicazione o in presenza di un downgrade dell&#39;autorizzazione da `ACPPlacesRequestAuthorizationLevelAlways` a `ACPPlacesRequestAuthorizationLevelWhenInUse` un&#39;autorizzazione, questo metodo non ha alcun effetto.

Il livello di autorizzazione può essere impostato su uno dei seguenti valori:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Richiede all&#39;utente l&#39;autorizzazione per utilizzare il servizio Places mentre l&#39;app è in uso. Il prompt dell&#39;utente contiene il testo della `NSLocationWhenInUseUsageDescription` chiave nel file info.plist dell&#39;app, e la presenza di tale chiave è necessaria quando si chiama questo metodo. Per ulteriori informazioni, consulta la documentazione [Apple su requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Utilizzate questo enum per richiedere il servizio Luoghi anche quando l&#39;app è in background. Devi avere le chiavi `NSLocationAlwaysUsageDescription` e nella `NSLocationWhenInUseUsageDescription` lista Info.plist dell&#39;app. Queste chiavi definiscono il testo che verrà visualizzato durante il prompt dell&#39;utente. Per ulteriori informazioni, consulta la documentazione [Apple su requestAlwaysAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` è il valore predefinito di autorizzazione della richiesta.

>[!IMPORTANT]
>
>L&#39;applicazione che ha autorizzato l&#39;uso dell&#39; `ACPPlacesRequestAuthorizationLevelWhenInUse` autorizzazione non attiverà eventi di ingresso/uscita sulle aree che si stanno verificando in background.

Di seguito sono riportati la sintassi e il codice di esempio per questa API:

#### Sintassi

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### Esempio

Per richiedere l&#39; `ACPPlacesRequestAuthorizationLevelWhenInUse` autorizzazione:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Per eseguire l&#39;aggiornamento all&#39; `ACPPlacesRequestAuthorizationLevelAlways` autorizzazione:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## Modalità di monitoraggio (solo iOS)

Il monitoraggio può essere impostato su uno dei seguenti valori:

* `ACPPlacesMonitorModeContinuous`

   L&#39;estensione di monitoraggio riceve ed elabora le posizioni più frequentemente. Questa strategia di monitoraggio consuma molta energia ma fornisce una maggiore precisione. Per ulteriori informazioni, consulta la documentazione [Apple sul monitoraggio](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)continuo.

* `ACPPlacesMonitorModeSignificantChanges`

   L&#39;estensione di monitoraggio riceve ed elabora gli aggiornamenti della posizione solo dopo che il dispositivo si è spostato a una distanza significativa dalla posizione precedentemente elaborata. Questa strategia di monitoraggio consuma meno energia rispetto alla strategia di monitoraggio continuo. Per ulteriori informazioni, consulta la documentazione [Apple sul monitoraggio significativo](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

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
