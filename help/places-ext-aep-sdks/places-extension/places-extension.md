---
title: Estensione Luoghi
description: L’estensione Luoghi consente di agire in base alla posizione degli utenti.
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 4%

---


# Estensione Luoghi {#places-extension}

L’estensione Luoghi consente di agire in base alla posizione degli utenti. Questa estensione è l&#39;interfaccia per le API del servizio Query Places. Ascoltando gli eventi che contengono le coordinate GPS e gli eventi dell&#39;area geografica, questa estensione invia nuovi eventi elaborati dal motore delle regole. L’estensione Luoghi inoltre recupera e fornisce un elenco del POI più vicino per i dati dell’app che recuperano dalle API. Le aree restituite dalle API vengono memorizzate nella cache e nella persistenza, il che consente un&#39;elaborazione offline limitata.

## Installare l&#39;estensione Luoghi in  Adobe Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Nella **[!UICONTROL Catalog]** scheda, individuare l’ **[!UICONTROL Places]** estensione e fare clic su **[!UICONTROL Install]**.
1. Selezionare le librerie Luoghi da utilizzare in questa proprietà. Queste sono le librerie che saranno accessibili nella tua app.
1. Fai clic su **[!UICONTROL Save]**.

   Quando fai clic su **[!UICONTROL Save]**, l’SDK del Experience Platform  cerca nei Servizi Luoghi i punti di interesse nelle librerie selezionate. I dati POI non vengono inclusi nel download della libreria al momento della creazione dell’app, ma un sottoinsieme di POI basato sulla posizione viene scaricato nel dispositivo dell’utente finale in fase di esecuzione e si basa sulle coordinate GPS dell’utente.

1. Completa il processo di pubblicazione per aggiornare la configurazione dell’SDK.

   Per ulteriori informazioni sulla pubblicazione in Experience Platform Launch, consultate [Pubblicazione](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Aggiungere l&#39;estensione Luoghi all&#39;app {#add-places-to-app}

Potete aggiungere l&#39;estensione Luoghi alle app Android e iOS. Di seguito sono riportati i passaggi per aggiungere Luoghi all&#39;applicazione iOS o Android. Le estensioni dei luoghi sono disponibili anche per le seguenti piattaforme. Per aggiungere Luoghi all&#39;applicazione durante lo sviluppo con una delle seguenti piattaforme, vedere i collegamenti di accompagnamento:

**[Plug-in Luoghi Cordova](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places Plugin](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Plug-in Luoghi Sfarfallio](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Plug-in Luoghi Xamarin](https://github.com/adobe/xamarin-acpcore)**


### Android

Per aggiungere l&#39;estensione Luoghi all&#39;app utilizzando Java:

1. Aggiungi l&#39;estensione Luoghi al progetto utilizzando il file gradle dell&#39;app.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importa l&#39;estensione Luoghi nell&#39;attività principale dell&#39;applicazione.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Per aggiungere l&#39;estensione Luoghi all&#39;app utilizzando Objective-C o Swift:

1. Aggiungi al progetto le librerie Luoghi e [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) . Dovrete aggiungere i seguenti contenitori `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   In alternativa, se non utilizzate i cococoapodi, potete includere manualmente le librerie Mobile Core e Luoghi dalla pagina [](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) delleversioni di Github.

1. Aggiornate i cocopodi:

   ```objective-c
   pod update
   ```

1. Aprite Xcode e, nella classe AppDelegate, importate le intestazioni Core e Places:

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Registra l’estensione Luoghi con Mobile Core {#register-places-mobile-core}

Devi registrare l&#39;estensione Luoghi con Mobile Core in Android e iOS.

#### Android

Nel metodo dell&#39;app `OnCreate` registrate le estensioni Luoghi:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Nel `application:didFinishLaunchingWithOptions:` metodo dell’app, registra l’estensione Luoghi con le altre chiamate di registrazione SDK:

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Modifica Tempo per la pubblicazione dell&#39;iscrizione Luoghi {#places-ttl}

I dati sulla posizione possono diventare rapidamente obsoleti, soprattutto se il dispositivo non riceve aggiornamenti sulla posizione in background.

Controlla il tempo di permanenza dei dati di appartenenza Luoghi sul dispositivo impostando l&#39;impostazione di `places.membershipttl` configurazione. Il valore passato rappresenta il numero di secondi per cui lo stato Luoghi rimarrà valido per il dispositivo.

#### Android

All’interno del callback di `MobileCore.start()` aggiornare la configurazione con le modifiche necessarie prima di chiamare `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Nella prima riga del callback del `ACPCore`metodo `start:` , chiama `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Chiavi di configurazione

Per aggiornare la configurazione SDK a livello di programmazione in fase di esecuzione, usa le informazioni seguenti per modificare i valori di configurazione dell&#39;estensione Places. Per ulteriori informazioni, consultate [Riferimento](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)API di configurazione.

| Chiave | Obbligatorio | Descrizione |
| :--- | :--- | :--- |
| `places.libraries` | Sì | Le librerie delle estensioni Luoghi per l&#39;app mobile. Specifica l&#39;ID libreria e il nome della libreria supportata dall&#39;app mobile. |
| `places.endpoint` | Sì | L’endpoint predefinito del servizio query Luoghi, utilizzato per ottenere informazioni sulle librerie e sui POI. |
| `places.membershipttl` | No | Valore predefinito di 3600 (secondi in un&#39;ora). Indica per quanto tempo, in secondi, le informazioni di appartenenza Luoghi per il dispositivo rimarranno valide. |
