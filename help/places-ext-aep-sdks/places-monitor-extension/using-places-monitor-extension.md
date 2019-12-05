---
title: Utilizzo dell’estensione Monitor luoghi
description: Informazioni su come installare, configurare e utilizzare l’estensione Places Monitor.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Utilizzo dell’estensione Monitor luoghi {#using-places-monitor-extension}

Per utilizzare l'estensione Luoghi monitor, completare le seguenti operazioni:

## Installare l’estensione Places Monitor in Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Nella **[!UICONTROL Catalog]** scheda, individuate l’ **[!UICONTROL Places Monitor]** estensione e fate clic su **Installa**.
1. Fai clic su **[!UICONTROL Save]**.
1. Segui il processo di pubblicazione per aggiornare la configurazione SDK.

### Configurare l’estensione Monitor luoghi {#configure-places-monitor-extension}

Non esistono attività di configurazione per l’estensione Monitor luoghi.

![configurare il ‌ di monitoraggio](/help/assets/configure_places_monitor.png)Luoghi

## Aggiungere l'estensione Luoghi Monitor all'app {#add-monitor-extension-to-app}

Dovete aggiungere l'estensione Places Monitor all'app Android o iOS.

### Android

In Android, completa i seguenti passaggi:

#### Java

1. Aggiungi l'estensione Places Monitor e l'estensione Places al progetto utilizzando il file gradle dell'app.

1. Includete anche i servizi Google Location più recenti nel file gradle.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importa l’estensione Places Monitor nell’attività principale dell’applicazione.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

In iOS, completa i seguenti passaggi:

1. Aggiungete la libreria al progetto tramite i cocoapodi `Podfile` aggiungendo `pod 'ACPPlacesMonitor'`.
1. Importare le librerie di monitor Luoghi e Luoghi:

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## Registrazione e avvio del monitor Luoghi {#register-start-places-monitor}

È necessario registrarsi e avviare il Monitor posizioni in Android o iOS.

## Android

In Android, completa i seguenti passaggi:

### Java

Nel metodo della tua app `OnCreate` registrati le estensioni Places Monitor:

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>Il monitoraggio dei luoghi dipende dall'estensione Luoghi. Quando installi manualmente l’estensione Monitor Luoghi, accertati di aggiungere anche la libreria `places.aar` al progetto.

## iOS

Nell'app iOS`application:didFinishLaunchingWithOptions`, registrati `PlacesMonitor` e posizioni con Mobile Core:

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>Il monitoraggio dei luoghi dipende dall'estensione Luoghi. When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## Aggiungere autorizzazioni al manifesto

### Android

**Java**

Per tutte le versioni di Android, per dichiarare che la tua app richiede l'autorizzazione di posizione, aggiungi un `<uses-permission>` elemento nel manifesto dell'app, come figlio dell' `<manifest>` elemento di livello principale. Per le applicazioni Android che hanno come destinazione API di livello 29 e superiore, per consentire all'app di accedere alla posizione in background, includete l'autorizzazione ACCESS_BACKGROUND_LOCATION.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Abilitare gli aggiornamenti della posizione in background {#enable-location-updates-background}

iOS supporta la distribuzione di eventi di posizione alle app che vengono sospese o che non sono più in esecuzione. Per ricevere gli aggiornamenti sulla posizione in background per l’estensione di Monitoraggio luoghi, configura la funzionalità di aggiornamento della posizione per l’app in `Xcode.background-location-updates`.

![utilizzo del monitor Luoghi](/help/assets/using-the-places-monitor_1.png)

## Configurazione delle chiavi plist

Nel `Info.plist` file dell'app devono essere incluse le seguenti chiavi:

* `NSLocationWhenInUseUsageDescription` - il testo deve descrivere il motivo per cui l'app richiede l'accesso alle informazioni sulla posizione dell'utente durante l'esecuzione in primo piano.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - il testo deve descrivere il motivo per cui l'app richiede l'accesso alle informazioni sulla posizione dell'utente in qualsiasi momento.

>[!TIP]
>
>Se l'app supporta iOS 10 e versioni precedenti, è necessaria anche la `NSLocationAlwaysUsageDescription` chiave.

![](/help/assets/using-the-places-monitor_2.png)
