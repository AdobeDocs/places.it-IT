---
title: Servizio Places
description: Places Service è un contesto importante per comprendere il coinvolgimento degli utenti di dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 10%

---

# Servizio Places {#home}

La posizione è un contesto importante per comprendere e interagire con gli utenti dei dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell’app e renderla un’esperienza più personalizzata e coinvolgente.

Places Service, precedentemente noto come Adobe Experience Platform Location Service, è un servizio di geolocalizzazione che consente alle app mobili dotate di awareness della posizione di contestualizzare quest&#39;ultima mediante l&#39;utilizzo di interfacce SDK avanzate e facili da usare, accompagnate da un database flessibile di punti di interesse (POI).

Places Service consente di ottenere quanto segue:

* Crea e gestisci un database di POI che può essere utilizzato con altre soluzioni Adobe Experience Cloud.
* Allega metadati personalizzati ai punti di interesse per renderli più ricchi e significativi specificando attributi aggiuntivi.
* Visualizza i punti di interesse su una mappa per comprendere facilmente il contesto spaziale e aggiungere/modificare gli attributi dei metadati.
* Configura l&#39;SDK in Adobe Experience Platform Launch per definire le regole attivate dalla posizione e le condizioni basate sui metadati.
* Riduci il codice da scrivere per monitorare la posizione di un dispositivo e utilizza l’estensione Luoghi per attivare automaticamente le regole specifiche per la posizione.

Questo ti consente di intraprendere azioni dai segnali di posizione in tempo reale, quando e dove conta. Il contesto giusto offre un’esperienza di coinvolgimento mobile più ricca.

Di seguito sono riportati alcuni modi per utilizzare Luoghi:

* Invia una notifica in tempo reale quando qualcuno entra in un POI, *&quot;Ehi.benvenuto allo stadio.&quot;*
* Analizza il traffico a piedi dei tuoi negozi rispetto ai tuoi negozi concorrenti.
* Segmenta un pubblico in base al comportamento offline utilizzando i profili di pubblico con contesto di posizione.
* Esegui il targeting di un utente con un&#39;esperienza in-store quando pertinente.

## Componenti di Places Service

Places Service comprende i seguenti componenti:

* **Servizio Web**

   Puoi creare e gestire i punti di interesse utilizzando le API REST di Luoghi. Per ulteriori informazioni sulle API REST, vedi [Gestire le librerie](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gestire i POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaccia di gestione POI**

   Visualizza i punti di interesse su una mappa per comprendere il contesto spaziale e aggiungere/modificare i punti di interesse e i relativi metadati personalizzati.

* **Estensione Luoghi**

   Interfaccia API mobile multipiattaforma per integrare il contesto della posizione nelle app mobili. Per ulteriori informazioni sugli SDK, vedi [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Regole di avvio**

   Regole di Launch geo-intelligenti che consentono di attivare azioni con eventi di entrata e uscita. Le regole consentono inoltre di utilizzare gli attributi geografici nelle condizioni per personalizzare l’esperienza.

## Terminologia

Di seguito sono riportati alcuni termini comuni utilizzati in questa documentazione:

* A **punto di interesse (POI)** è una geolocalizzazione di interesse per la tua organizzazione.

   Puoi definire punti di interesse con attributi quali nome, raggio, indirizzo, categoria e tag metadati.

* A **geofence** è un tipo di POI.

   Questo tipo di POI è un limite geografico virtuale definito dalle coordinate di latitudine e longitudine.

* A **beacon** è un tipo di POI.

   Questo tipo di POI è un dispositivo fisico che rappresenta una posizione emettendo un segnale Bluetooth a bassa potenza. Il supporto dei beacon verrà rilasciato in una versione futura.

* Una **libreria** è una raccolta di POI, raggruppati per associare facilmente le regole a un set invece di un POI.

* Un **estensione** è l’estensione di Experience Platform Launch necessaria per integrare l’SDK di Places nelle app mobili.

   Estensione utilizzata con gli altri SDK per dispositivi mobili per aggiungere contesto di posizione alle esperienze.

* Un’**organizzazione** è l’entità Adobe che identifica la società dell’utente in Adobe Experience Cloud.

   In genere, un&#39;organizzazione corrisponde al nome dell&#39;azienda. Tuttavia, un&#39;azienda può avere più di un&#39;organizzazione. L’amministratore dell’organizzazione può configurare gruppi e utenti e configurare la funzionalità single sign-on.

* L’**orgID** è l’ID che rappresenta l’organizzazione dell’utente in Adobe Experience Platform.

   Per ulteriori informazioni, consulta [Ricerca dell&#39;orgID](https://forums.adobe.com/thread/2339895).

* La **ID Experience Cloud** Il servizio fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni dell&#39;Experience Cloud.

   Per maggiori informazioni, consulta [Panoramica](https://docs.adobe.com/content/help/it-IT/id-service/using/intro/overview.html).
