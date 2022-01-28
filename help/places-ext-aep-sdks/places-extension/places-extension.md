---
title: Estensione Luoghi
description: L’estensione Luoghi consente di agire in base alla posizione degli utenti.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 4%

---

# Estensione Luoghi {#places-extension}

L’estensione Luoghi consente di agire in base alla posizione degli utenti. Questa estensione è l’interfaccia delle API di Places Query Service. Ascoltando gli eventi che contengono le coordinate GPS e gli eventi dell&#39;area geografica, questa estensione invia nuovi eventi elaborati dal motore di regole. L’estensione Places recupera e fornisce anche un elenco dei punti di interesse più vicini per i dati dell’app recuperati dalle API. Le aree restituite dalle API vengono memorizzate nella cache e nella persistenza, il che consente un’elaborazione offline limitata.

## Installare l’estensione Luoghi in Adobe Experience Platform Launch

1. In Experience Platform Launch, fai clic sul pulsante **[!UICONTROL Estensioni]** scheda .
1. Sulla **[!UICONTROL Catalogo]** , individua la **[!UICONTROL Luoghi]** e fai clic su **[!UICONTROL Installa]**.
1. Seleziona le librerie Luoghi da utilizzare in questa proprietà. Queste sono le librerie che saranno accessibili nella tua app.
1. Fai clic su **[!UICONTROL Salva]**.

   Quando fai clic su **[!UICONTROL Salva]**, l’SDK di Experience Platform cerca i punti di interesse nei servizi Places nelle librerie selezionate. I dati POI non vengono inclusi nel download della libreria quando crei l’app, ma un sottoinsieme di POI basato sulla posizione viene scaricato sul dispositivo dell’utente finale in fase di esecuzione e si basa sulle coordinate GPS dell’utente.

1. Completa il processo di pubblicazione per aggiornare la configurazione SDK.

   Per ulteriori informazioni sulla pubblicazione in Experience Platform Launch, consulta [Pubblicazione](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Configurare l’estensione Luoghi {#configure-places-extension}

![](/help/assets/places-extension.png)

## Aggiungere l’estensione Luoghi all’app {#add-places-to-app}

Puoi aggiungere l’estensione Luoghi alle app Android e iOS. Di seguito sono riportati i passaggi per aggiungere Luoghi all’applicazione iOS o Android. Le estensioni di Luoghi sono disponibili anche per le seguenti piattaforme. Per l’aggiunta di Luoghi all’applicazione durante lo sviluppo con una di queste piattaforme, consulta i relativi collegamenti:

**[Plug-in Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places Plugin](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Plugin Luoghi di flutter](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Plug-in di Xamarin Places](https://github.com/adobe/xamarin-acpcore)**


### Android

Per aggiungere l’estensione Luoghi all’app utilizzando Java:

1. Aggiungi l’estensione Luoghi al progetto utilizzando il file gradle dell’app.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importa l&#39;estensione Luoghi nell&#39;attività principale dell&#39;applicazione.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Per aggiungere l’estensione Luoghi all’app utilizzando Objective-C o Swift:

1. Aggiungi Luoghi e [Core mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) librerie al tuo progetto. Dovrai aggiungere i seguenti pod al tuo `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   In alternativa, se non utilizzi Cocoapods, puoi includere manualmente le librerie Mobile Core e Places dal nostro [pagina delle versioni](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) su Github.

1. Aggiorna i Cocoapods:

   ```objective-c
   pod update
   ```

1. Apri Xcode e nella classe AppDelegate importa le intestazioni Core e Places:

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

### Registra l&#39;estensione Luoghi con Mobile Core {#register-places-mobile-core}

Devi registrare l’estensione Luoghi con Mobile Core in Android e iOS.

#### Android

Nelle app `OnCreate` registra le estensioni Luoghi:

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

Nelle app `application:didFinishLaunchingWithOptions:` registra l&#39;estensione Places con le altre chiamate di registrazione SDK:

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

### Modifica della durata dell’iscrizione a Luoghi {#places-ttl}

I dati sulla posizione possono diventare rapidamente obsoleti, soprattutto se il dispositivo non riceve aggiornamenti sulla posizione in background.

Controlla il tempo di esecuzione dei dati di appartenenza di Places sul dispositivo impostando il `places.membershipttl` impostazione di configurazione. Il valore passato rappresenta il numero di secondi in cui lo stato Luoghi rimarrà valido per il dispositivo.

#### Android

All&#39;interno del callback di `MobileCore.start()` aggiorna la configurazione con le modifiche necessarie prima di richiamare `lifecycleStart`:

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

Sulla prima riga del callback di `ACPCore`s `start:` metodo, chiamata `updateConfiguration:`

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

Per aggiornare programmaticamente la configurazione dell’SDK in fase di runtime, usa le seguenti informazioni per modificare i valori di configurazione dell’estensione Places. Per ulteriori informazioni, consulta [Riferimento API di configurazione](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Chiave | Obbligatorio | Descrizione |
| :--- | :--- | :--- |
| `places.libraries` | Sì | Le librerie di estensioni Luoghi per l’app mobile. Specifica l&#39;ID libreria e il nome della libreria supportata dall&#39;app mobile. |
| `places.endpoint` | Sì | L’endpoint predefinito del servizio Query Luoghi, utilizzato per ottenere informazioni su librerie e POI. |
| `places.membershipttl` | No | Valore predefinito di 3600 (secondi in un&#39;ora). Indica per quanto tempo, in secondi, le informazioni di iscrizione a Places per il dispositivo rimarranno valide. |
