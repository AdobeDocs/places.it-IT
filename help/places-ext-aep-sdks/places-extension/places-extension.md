---
title: Estensione Luoghi
seo-title: Estensione Luoghi
description: L’estensione Luoghi consente di agire in base alla posizione degli utenti.
seo-description: L’estensione Luoghi consente di agire in base alla posizione degli utenti.
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Estensione Luoghi {#places-extension}

L’estensione Luoghi consente di agire in base alla posizione degli utenti. Questa estensione è l'interfaccia per le API del servizio Query Places. Ascoltando gli eventi che contengono le coordinate GPS e gli eventi dell'area geografica, questa estensione invia nuovi eventi elaborati dal motore delle regole. L’estensione Luoghi inoltre recupera e fornisce un elenco del POI più vicino per i dati dell’app che recuperano dalle API. Le aree restituite dalle API vengono memorizzate nella cache e nella persistenza, il che consente un'elaborazione offline limitata.

## Installa l’estensione Places in Adobe Experience Platform Launch

1. In Experience Platform Launch, fai clic sulla **[!UICONTROL Extensions]** scheda.
2. Nella **[!UICONTROL Catalog]** scheda, individuare l’ **[!UICONTROL Adobe Places]** estensione e fare clic su **[!UICONTROL Install]**.
3. Selezionare le librerie Luoghi da utilizzare in questa proprietà. Queste sono le librerie che saranno accessibili nella tua app.
4. Fai clic su **[!UICONTROL Save]**.

   Quando fai clic su **[!UICONTROL Save]**, l’SDK di Experience Platform cerca nei Servizi Luoghi i punti di interesse nelle librerie selezionate. I dati POI non vengono inclusi nel download della libreria al momento della creazione dell’app, ma un sottoinsieme di POI basato sulla posizione viene scaricato nel dispositivo dell’utente finale in fase di esecuzione e si basa sulle coordinate GPS dell’utente.

5. Completa il processo di pubblicazione per aggiornare la configurazione SDK.

   Per ulteriori informazioni sulla pubblicazione in Experience Platform Launch, consultate [Pubblicazione](https://docs.adobelaunch.com/launch-reference/publishing).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Aggiungere l'estensione Luoghi all'app {#add-places-to-app}

Potete aggiungere l'estensione Luoghi alle app Android e iOS.

### Android

Per aggiungere l'estensione Luoghi all'app utilizzando Java:

1. Aggiungi l'estensione Luoghi al progetto utilizzando il file gradle dell'app.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

2. Importa l'estensione Luoghi nell'attività principale dell'applicazione.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Per aggiungere l'estensione Luoghi all'app utilizzando Objective-C o Swift:

1. Aggiungi al progetto le librerie Luoghi e [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) . Dovrete aggiungere i seguenti contenitori `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   In alternativa, se non utilizzate i cococoapodi, potete includere manualmente le librerie Mobile Core e Luoghi dalla pagina [delle](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) versioni di Github.

2. Aggiornate i cocopodi:

   ```objective-c
   pod update
   ```

3. Apri Xcode e nella classe AppDelegate importa le intestazioni Core e Places:

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

### Registra luoghi con core mobile {#register-places-mobile-core}

Devi registrare Luoghi con Mobile Core in Android e iOS.

#### Android

Nel metodo della tua app `OnCreate` registrati le estensioni Location Services:

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

## Chiavi di configurazione

Per aggiornare la configurazione SDK a livello di programmazione in fase di esecuzione, usa le informazioni seguenti per modificare i valori di configurazione di Places. Per ulteriori informazioni, consultate [Riferimento](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)API di configurazione.

| Chiave | Obbligatorio | Descrizione |
| :--- | :--- | :--- |
| `places.libraries` | Sì | Inserisce le librerie per l'app mobile. Specifica l'ID libreria e il nome della libreria supportata dall'app mobile. |
| `places.endpoint` | Sì | L’endpoint predefinito del servizio Query posizione della piattaforma esperienza, utilizzato per ottenere informazioni sulle librerie e sui POI. |

