---
title: Utilizzo di Luoghi con Mobile Services per la messaggistica
seo-title: Utilizzo di Luoghi con Mobile Services per la messaggistica
description: In questa sezione viene illustrato come utilizzare Places con Mobile Services per la messaggistica.
seo-description: In questa sezione viene illustrato come utilizzare Places con Mobile Services per la messaggistica.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Adobe Mobile Services {#places-mobile-services}

Prima di poter utilizzare l'estensione Mobile Services per la messaggistica, verifica i seguenti prerequisiti:

* I punti di interesse sono stati creati in Location Service. Se necessario, consultare la documentazione. (collegamento alla creazione di un POI)Nota: Il servizio Location include un nuovo e migliorato database dei punti di interesse per l'organizzazione esistente al di fuori dell'interfaccia AMS legacy. Qualsiasi POI trovato nella navigazione "Gestisci luoghi" di AMS funzionerà solo per la versione 4 dell’SDK.
   * Di seguito è riportata l’interfaccia legacy di gestione dei POI di Luoghi in AMS per le versioni precedenti dell’SDK:

      ![Interfaccia utente precedente](/help/assets/legacy-location-v4-ui.png)

   * Interfaccia di gestione di Location Service POI:

      ![Interfaccia utente di gestione POI del servizio Posizione](/help/assets/places-ui.png)

* L’SDK ACP è configurato correttamente con le estensioni Places e/o Places Monitor. Ciò significa che i dati sono disponibili come eventi e/o condizioni nel motore delle regole di Launch per la tua app mobile. Se necessario, consulta la documentazione. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Scopri come creare e pubblicare le regole di Launch nell’SDK ACP nella tua app mobile. Se necessario, consulta la documentazione. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Launch Data Elements viene creato dai dati di estensione SDK Places che verranno utilizzati nelle regole. Consultate la documentazione (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## Reporting

Prima di poter utilizzare il reporting, è necessario soddisfare i seguenti prerequisiti:

* Invio dei dati del servizio di localizzazione alla suite di rapporti di Adobe Analytics riuscito. Se necessario, visita la documentazione di Adobe Analytics (collegamento ai documenti di Steve).
* Familiare con i report AMS. Se necessario, visitate la documentazione (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## Visualizzazione rapporti

Puoi eseguire i rapporti AMS utilizzando i dati del servizio di localizzazione inviati ad Adobe Analytics. Ad esempio, ho inviato degli eventi quando gli utenti dispongono di voci in uno dei miei POI. In questo rapporto ho aggiunto un filtro per l’evento POI sopra al mio rapporto utente out-of-the-box:

![Visualizzazione report](/help/assets/report-visualize.png)

Ulteriori flessibilità nella visualizzazione dei dati del servizio di localizzazione sono disponibili nelle interfacce di Adobe Analytics.

