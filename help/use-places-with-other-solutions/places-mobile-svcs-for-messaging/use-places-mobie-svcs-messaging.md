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
   >Il servizio Places include un database POI nuovo e migliorato per la tua organizzazione che esiste al di fuori dell’interfaccia utente legacy di Mobile Services. POI che si trovano su Mobile Services *Gestisci posizioni* la navigazione tra le pagine funziona solo per la versione 4 dell’SDK.

* Qui è *Gestire i luoghi* Pagina di gestione dei POI nell’interfaccia utente di Mobile Services legacy per le versioni precedenti dell’SDK:

   ![Interfaccia utente legacy](/help/assets/legacy-location-v4-ui.png)

* Interfaccia utente di Places Service:

   ![Interfaccia utente di gestione POI di Places Service](/help/assets/places-ui.png)

* L’SDK ACP è configurato correttamente con l’estensione Luoghi.

   Ciò significa che i dati sono disponibili come eventi e/o condizioni nel motore delle regole di Experience Platform Launch per la tua app mobile. Per ulteriori informazioni, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Acquisisci familiarità con la creazione e la pubblicazione delle regole del Experience Platform Launch nell’SDK ACP nella tua app mobile.

   Per ulteriori informazioni, consulta [Motore a regole](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Gli elementi dati di Experience Platform Launch vengono creati dai dati di estensione Luoghi che verranno utilizzati nel motore Regole.

   Per ulteriori informazioni, consulta [Elementi dati](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Generazione rapporti

Prima di poter utilizzare i rapporti, completa i seguenti prerequisiti:

* Invio dei dati del servizio Places alla suite di rapporti di Adobe Analytics completato.

   Per ulteriori informazioni, consulta [Utilizzare il servizio Places con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Acquisisci familiarità con i rapporti di Mobile Services.

   Per ulteriori informazioni, consulta [Rapporti](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualizzazione rapporti

Puoi eseguire i rapporti di Mobile Services utilizzando i dati di Places Service inviati ad Adobe Analytics. Nell’esempio seguente, gli eventi vengono inviati quando gli utenti hanno partecipazioni in uno dei POI. In questo rapporto è stato aggiunto un filtro dell’evento POI entry nel rapporto utente predefinito:

![Visualizzazione dei rapporti](/help/assets/report-visualize.png)

Nelle interfacce Adobe Analytics è disponibile un’ulteriore flessibilità nella visualizzazione dei dati di Places Service.
