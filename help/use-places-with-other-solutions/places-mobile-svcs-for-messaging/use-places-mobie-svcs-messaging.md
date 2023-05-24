---
title: Utilizzo di Places Service con Mobile Services per la messaggistica
description: Questa sezione illustra come utilizzare Places Service con Mobile Services per la messaggistica.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Prima di poter utilizzare l’estensione Mobile Services per la messaggistica, controlla i seguenti prerequisiti:

* I punti di interesse sono stati creati in Places Service. Per ulteriori informazioni, consulta [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Il servizio Places include un database dei punti di interesse nuovo e migliorato per l’organizzazione, che esiste al di fuori dell’interfaccia utente legacy di Mobile Services. POI che si trovano sul servizio mobile *Gestisci luoghi* la navigazione delle pagine funziona solo per la versione 4 dell’SDK.

* Ecco il *Gestisci luoghi* Pagina di gestione POI nell&#39;interfaccia utente legacy di Mobile Services per le versioni precedenti dell&#39;SDK:

   ![Interfaccia precedente](/help/assets/legacy-location-v4-ui.png)

* Di seguito è riportata l’interfaccia utente di Places Service:

   ![Interfaccia utente di gestione POI di Places Service](/help/assets/places-ui.png)

* L’SDK ACP è configurato correttamente con l’estensione Luoghi.

   Ciò significa che i dati sono disponibili come eventi e/o condizioni nel motore delle regole di Experience Platform Launch per la tua app mobile. Per ulteriori informazioni, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Acquisisci familiarità con la creazione e la pubblicazione di regole di Experience Platform Launch nell’SDK del provider di servizi di audioconferenza nell’app mobile.

   Per ulteriori informazioni, consulta [Motore di regole](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Gli elementi dati di Experience Platform Launch vengono creati dai dati dell’estensione Luoghi che verranno utilizzati nel motore delle regole.

   Per ulteriori informazioni, consulta [Elementi dati](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Generazione rapporti

Prima di poter utilizzare il reporting, completa i seguenti prerequisiti:

* Invio dei dati di Places Service alla suite di rapporti di Adobe Analytics completato.

   Per ulteriori informazioni, consulta [Utilizzare Places Service con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Acquisisci familiarità con i rapporti di Mobile Services.

   Per ulteriori informazioni, consulta [Rapporti](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualizzazione reporting

Puoi eseguire rapporti di Mobile Services utilizzando i dati di Places Service inviati ad Adobe Analytics. Nell’esempio seguente, gli eventi vengono inviati quando gli utenti dispongono di voci in uno dei POI. In questo rapporto è stato aggiunto un filtro dell’evento di ingresso POI sul rapporto utente preconfigurato:

![Visualizzazione dei rapporti](/help/assets/report-visualize.png)

Nelle interfacce Adobe Analytics è disponibile un’ulteriore flessibilità nella visualizzazione dei dati di Places Service.
