---
title: Utilizzo di Places Service con Mobile Services per la messaggistica
description: Questa sezione illustra come utilizzare Places Service con Mobile Services per la messaggistica.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
TQID: https://experienceleague.adobe.com/-axuli6p-QHthMkucGLCcgyHCqrwudXmif-dZwpGli4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 359
ht-degree: 3%

---

# Adobe Mobile Services {#places-mobile-services}

Prima di poter utilizzare l’estensione Mobile Services per la messaggistica, controlla i seguenti prerequisiti:

* I punti di interesse sono stati creati in Places Service. Per ulteriori informazioni, vedere [Creare un punto di interesse](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >Il servizio Places include un database dei punti di interesse nuovo e migliorato per l’organizzazione, che esiste al di fuori dell’interfaccia utente legacy di Mobile Services. I POI che si trovano nel servizio mobile *Gestione luoghi* funzioneranno solo per la versione 4 di SDK.

* Ecco la pagina di gestione dei punti di interesse *Gestisci luoghi* nell&#39;interfaccia utente legacy di Mobile Services per le versioni precedenti di SDK:

  ![Interfaccia precedente](/help/assets/legacy-location-v4-ui.png)

* Di seguito è riportata l’interfaccia utente di Places Service:

  ![Interfaccia utente di gestione punti di interesse di Places Service](/help/assets/places-ui.png)

* ACP SDK è configurato correttamente con l’estensione Luoghi.

  Ciò significa che i dati sono disponibili come eventi e/o condizioni nel motore delle regole di Experience Platform Launch per la tua app mobile. Per ulteriori informazioni, vedere [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Acquisisci familiarità con la creazione e la pubblicazione di regole di Experience Platform Launch nel SDK ACP nella tua app mobile.

  Per ulteriori informazioni, vedere [Motore regole](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Gli elementi dati di Experience Platform Launch vengono creati dai dati dell’estensione Luoghi che verranno utilizzati nel motore delle regole.

  Per ulteriori informazioni, vedere [Elementi dati](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Generazione dei rapporti

Prima di poter utilizzare il reporting, completa i seguenti prerequisiti:

* Invio dei dati di Places Service alla suite di rapporti di Adobe Analytics completato.

  Per ulteriori informazioni, vedere [Utilizzare Places Service con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Acquisisci familiarità con i rapporti di Mobile Services.

  Per ulteriori informazioni, vedere [Report](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=it).

## Visualizzazione reporting

Puoi eseguire rapporti di Mobile Services utilizzando i dati di Places Service inviati ad Adobe Analytics. Nell’esempio seguente, gli eventi vengono inviati quando gli utenti dispongono di voci in uno dei POI. In questo rapporto è stato aggiunto un filtro dell’evento di ingresso POI sul rapporto utente preconfigurato:

![Visualizzazione report](/help/assets/report-visualize.png)

Nelle interfacce Adobe Analytics è disponibile un’ulteriore flessibilità nella visualizzazione dei dati di Places Service.
