---
title: Servizio Places
description: Places Service è un contesto importante per comprendere il coinvolgimento degli utenti di dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Servizio Places {#home}

La posizione è un contesto importante per comprendere e coinvolgere gli utenti mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.

Places Service, precedentemente noto come Adobe Experience Platform Location Service, è un servizio di geolocalizzazione che consente alle app mobili dotate di awareness della posizione di contestualizzare quest’ultima mediante l’uso di interfacce SDK avanzate e facili da usare, associate a un database flessibile di punti di interesse (POI).

Places Service consente di ottenere quanto segue:

* Crea e gestisci un database di POI che possono essere utilizzati con altre soluzioni Adobe Experience Cloud.
* Allega i metadati personalizzati ai POI per renderli più ricchi e significativi specificando attributi aggiuntivi.
* Visualizza i punti di interesse su una mappa per comprendere facilmente il contesto spaziale e aggiungere/modificare gli attributi dei metadati.
* Configura l&#39;SDK in Adobe Experience Platform Launch per definire le regole attivate dalla posizione e le condizioni basate sui metadati.
* Riduci il codice da scrivere per monitorare la posizione di un dispositivo e utilizza l’estensione Luoghi per attivare automaticamente le regole specifiche della posizione.

Questo ti consentirà di intraprendere azioni dai segnali di posizione in tempo reale, quando e dove sono importanti. Il contesto giusto offre un’esperienza di coinvolgimento mobile più coinvolgente.

Di seguito sono riportati alcuni dei modi in cui è possibile utilizzare Places:

* Invia una notifica in tempo reale quando qualcuno entra in un punto di interesse, *&quot;Hey.benvenuto allo stadio.&quot;*
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

* Un&#39;estensione **extension** è l&#39;estensione di Experience Platform Launch necessaria per integrare l&#39;SDK Places nelle app mobili.

  Estensione utilizzata con gli altri SDK per dispositivi mobili per aggiungere contesto di posizione alle esperienze.

* Un’**organizzazione** è l’entità Adobe che identifica la società dell’utente in Adobe Experience Cloud.

  In genere, un’organizzazione è il nome della tua azienda. Tuttavia, un’azienda può avere più di un’organizzazione. L&#39;amministratore dell&#39;organizzazione può configurare gruppi e utenti e configurare la funzionalità Single Sign-On.

* L’**orgID** è l’ID che rappresenta l’organizzazione dell’utente in Adobe Experience Platform.

  Per ulteriori informazioni, consulta [Ricerca dell&#39;orgID](https://forums.adobe.com/thread/2339895).

* Il servizio **ID Experience Cloud** fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni dell&#39;Experience Cloud.

  Per maggiori informazioni, consulta [Panoramica](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=it).

