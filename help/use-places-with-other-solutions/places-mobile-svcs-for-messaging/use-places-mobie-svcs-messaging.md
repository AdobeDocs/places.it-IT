---
title: Utilizzo di Places Service con Mobile Services per la messaggistica
description: In questa sezione viene illustrato come utilizzare Places Service con Mobile Services per la messaggistica.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

Prima di poter utilizzare l&#39;estensione Mobile Services per la messaggistica, verifica i seguenti prerequisiti:

* I punti di interesse sono stati creati in Places Service. For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Il servizio Places include un nuovo database POI migliorato per la tua organizzazione che esiste al di fuori dell’interfaccia utente di Mobile Services legacy. I POI che si trovano nella navigazione della pagina *Gestisci posizionamenti* di Mobile Service funzionano solo per la versione 4 dell’SDK.

* Di seguito è riportata la pagina di gestione *Manage Places* POI (Gestisci punti di interesse) dell&#39;interfaccia utente di Mobile Services precedente per le versioni precedenti dell&#39;SDK:

   ![Interfaccia utente precedente](/help/assets/legacy-location-v4-ui.png)

* Interfaccia utente del servizio Luoghi:

   ![Interfaccia utente di gestione dei punti di servizio](/help/assets/places-ui.png)

* L’SDK ACP è configurato correttamente con le estensioni Places Service e/o Places Monitor.

   Ciò significa che i dati sono disponibili come eventi e/o condizioni nel motore delle regole Experience Platform Launch per la tua app mobile. Per ulteriori informazioni, consultate Estensione [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Luoghi o Estensione [Monitor](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)Luoghi.

* Acquisisci familiarità con la creazione e la pubblicazione di regole Experience Platform Launch nell’SDK ACP nella tua app mobile.

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Gli elementi di dati di avvio della piattaforma esperienza vengono creati dai dati di estensione Luoghi che verranno utilizzati nel motore Regole.

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Reporting

Prima di poter utilizzare il reporting, è necessario soddisfare i seguenti prerequisiti:

* Invio dei dati del servizio Luoghi alla suite di rapporti di Adobe Analytics completato.

   Per ulteriori informazioni, consulta [Utilizzare i servizi Luoghi con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Acquisisci familiarità con i rapporti di Mobile Services.

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualizzazione rapporti

Puoi eseguire i rapporti di Mobile Services utilizzando i dati di Places Service inviati ad Adobe Analytics. Nell’esempio seguente, gli eventi vengono inviati quando gli utenti dispongono di voci in uno dei POI. In questo rapporto è stato aggiunto un filtro dell’evento POI nel rapporto sugli utenti out-of-the-box:

![Visualizzazione report](/help/assets/report-visualize.png)

Ulteriori flessibilità nella visualizzazione dei dati del servizio Places sono disponibili nelle interfacce Adobe Analytics.

