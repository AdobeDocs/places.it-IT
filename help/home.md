---
title: Servizio Places
description: Places Service è un contesto importante per comprendere il coinvolgimento degli utenti di dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
TQID: https://experienceleague.adobe.com/4kI1AuV2l-qfC3mOrcsoG9NDRcOPJBdkWPmKkQuDIJk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 684
ht-degree: 9%

---

# Servizio Places {#home}

La posizione è un contesto importante per comprendere e coinvolgere gli utenti mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.

Places Service, precedentemente noto come Adobe Experience Platform Location Service, è un servizio di geolocalizzazione che consente alle app mobili dotate di awareness della posizione di contestualizzare quest’ultima mediante l’uso di interfacce SDK avanzate e facili da usare, associate a un database flessibile di punti di interesse (POI).

Places Service consente di ottenere quanto segue:

* Crea e gestisci un database di POI che possono essere utilizzati con altre soluzioni Adobe Experience Cloud.
* Allega i metadati personalizzati ai POI per renderli più ricchi e significativi specificando attributi aggiuntivi.
* Visualizza i punti di interesse su una mappa per comprendere facilmente il contesto spaziale e aggiungere/modificare gli attributi dei metadati.
* Configura SDK in Adobe Experience Platform Launch per definire le regole attivate dalla posizione e le condizioni basate sui metadati.
* Riduci il codice da scrivere per monitorare la posizione di un dispositivo e utilizza l’estensione Luoghi per attivare automaticamente le regole specifiche della posizione.

Questo ti consentirà di intraprendere azioni dai segnali di posizione in tempo reale, quando e dove sono importanti. Il contesto giusto offre un’esperienza di coinvolgimento mobile più coinvolgente.

Di seguito sono riportati alcuni dei modi in cui è possibile utilizzare Places:

* Invia una notifica in tempo reale quando qualcuno entra in un punto di interesse, *&quot;Ciao..benvenuto allo stadio.&quot;*
* Analizza il traffico a piedi dei tuoi negozi rispetto a quelli della concorrenza.
* Segmentare un pubblico in base al comportamento offline utilizzando profili di pubblico con contesto di posizione.
* Se necessario, rivolgiti a un utente con un’esperienza in-store.

## Componenti di Places Service

Places Service include i seguenti componenti:

* **Servizio Web**

  Puoi creare e gestire i punti di interesse utilizzando le API REST di Places. Per ulteriori informazioni sulle API REST, consulta [Gestire le librerie](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gestire i punti di interesse](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaccia di gestione POI**

  Visualizza i POI su una mappa per comprendere il contesto spaziale e aggiungere/modificare i POI e i relativi metadati personalizzati.

* **Estensione Luoghi**

  L’interfaccia API mobile multipiattaforma per integrare il contesto della posizione nelle app mobili. Per ulteriori informazioni sugli SDK, consulta [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Regole di avvio**

  Le regole di Launch geo-intelligenti che consentono di attivare azioni con eventi di entrata e uscita. Le regole ti consentono inoltre di utilizzare gli attributi geografici in condizioni per personalizzare l’esperienza.

## Terminologia

Di seguito sono riportati alcuni termini comuni utilizzati in questa documentazione:

* Un **punto di interesse (POI)** è una geolocalizzazione di interesse per la tua organizzazione.

  Puoi definire punti di interesse con attributi quali nome, raggio, indirizzo, categoria e tag di metadati.

* Un **recinto geografico** è un tipo di POI.

  Questo tipo di punto di interesse è un limite geografico virtuale definito dalle coordinate di latitudine e longitudine.

* Un **beacon** è un tipo di POI.

  Questo tipo di punto di interesse è un dispositivo fisico che rappresenta una posizione emettendo un segnale Bluetooth a basso consumo. Il supporto dei beacon sarà disponibile in una versione futura.

* Una **libreria** è una raccolta di POI, raggruppati per associare facilmente le regole a un set invece di un POI.

* Un&#39;estensione **extension** è l&#39;estensione Experience Platform Launch necessaria per integrare Places SDK nelle app mobili.

  Estensione utilizzata con gli altri SDK per dispositivi mobili per aggiungere contesto di posizione alle esperienze.

* Un’**organizzazione** è l’entità Adobe che identifica la società dell’utente in Adobe Experience Cloud.

  In genere, un’organizzazione è il nome della tua azienda. Tuttavia, un’azienda può avere più di un’organizzazione. L&#39;amministratore dell&#39;organizzazione può configurare gruppi e utenti e configurare la funzionalità Single Sign-On.

* L’**orgID** è l’ID che rappresenta l’organizzazione dell’utente in Adobe Experience Platform.

  Per ulteriori informazioni, consulta [Ricerca dell&#39;orgID](https://forums.adobe.com/thread/2339895).

* Il servizio **Experience Cloud ID** fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni di Experience Cloud.

  Per maggiori informazioni, consulta [Panoramica](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=it).

