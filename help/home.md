---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: 'Location Service è un contesto importante per comprendere il coinvolgimento degli utenti di dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell''app e renderla un''esperienza più personalizzata e coinvolgente. '
seo-description: 'Location Service è un contesto importante per comprendere il coinvolgimento degli utenti di dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell''app e renderla un''esperienza più personalizzata e coinvolgente. '
translation-type: tm+mt
source-git-commit: ecb059400d9203884faab6fd2f627251eeaeea38

---


# Panoramica di Adobe Experience Platform Location Service {#home}

!["Adobe Experience Platform Location Service"](/help/assets/LocationHeader.png)

La posizione è un contesto importante per comprendere e coinvolgere gli utenti dei dispositivi mobili. Utilizzando questo contesto, gli sviluppatori di app mobili possono migliorare la progettazione dell'app e renderla un'esperienza più personalizzata e coinvolgente.

Adobe Experience Platform Location Service (Location Service) è un servizio di geolocalizzazione che consente alle app mobili con consapevolezza della posizione di comprendere il contesto della posizione mediante l’uso di interfacce SDK ricche e facili da usare, accompagnate da un database flessibile di punti di interesse (POI).

Location Service consente di ottenere quanto segue:

* Crea e gestisci un database di POI che puoi sfruttare con altre soluzioni Adobe Experience Cloud.
* Allegate metadati personalizzati ai POI per renderli più ricchi e significativi specificando attributi aggiuntivi.
* Visualizzate i POI su una mappa per comprendere facilmente il contesto spaziale e aggiungere/modificare gli attributi dei metadati.
* Configura l’SDK in Adobe Experience Platform Launch per definire le regole attivate dalla posizione e le condizioni basate sui metadati.
* Ridurre il codice da scrivere per monitorare la posizione di un dispositivo e utilizzare l'estensione Luoghi per attivare automaticamente le regole specifiche per la posizione.

In questo modo potrete eseguire azioni dai segnali di posizione in tempo reale, quando e dove sono importanti. Il contesto giusto offre un'esperienza di coinvolgimento mobile più arricchente.

Di seguito sono riportati alcuni modi per utilizzare i Luoghi:

* Invia una notifica in tempo reale quando qualcuno entra in un POI, *"Hey.benvenuto allo stadio."*
* Analizzare il traffico di pedoni tra i negozi e i negozi concorrenti.
* Segmentate un'audience in base al comportamento offline utilizzando i profili di audience con contesto della posizione.
* Esegue il targeting di un utente con un'esperienza in-store quando pertinente.

## Componenti di Location Service

Il servizio di localizzazione comprende i seguenti componenti:

* **Servizio Web**

   Potete creare e gestire i POI utilizzando le API REST di Luoghi. Per ulteriori informazioni sulle API REST, consultate [Gestire le librerie](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gestire i POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaccia di gestione POI**

   Visualizzare i POI su una mappa per comprendere il contesto spaziale e aggiungere o modificare i POI e i relativi metadati personalizzati.

* **Estensione Luoghi**

   L'interfaccia API mobile multipiattaforma per integrare il contesto della posizione nelle app mobili. Per ulteriori informazioni sugli SDK, vedi Estensione [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

* **Regole di avvio**

   Regole di Launch geo-intelligenti che consentono di attivare azioni con eventi di entrata e uscita. Le regole consentono inoltre di utilizzare gli attributi geografici in condizioni per personalizzare l'esperienza.

* **Estensione Luoghi monitor**

   L’SDK per dispositivi mobili multipiattaforma che può essere incorporato nell’app mobile per monitorare automaticamente i cambiamenti di posizione dell’utente e attivare le regole di posizione. Per ulteriori informazioni, consultate Estensione [Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)posizioni.

## Terminologia

Di seguito sono riportati alcuni termini comuni utilizzati nella documentazione:

* Un **punto di interesse (POI)** è una geolocalità che interessa la tua organizzazione.

   Potete definire i POI con attributi quali nome, raggio, indirizzo, categoria e tag di metadati.

* Una **geofence** è un tipo di POI.

   Questo tipo di POI è un limite geografico virtuale definito dalle coordinate di latitudine e longitudine.

* Un **beacon** è un tipo di POI.

   Questo tipo di POI è un dispositivo fisico che rappresenta una posizione emettendo un segnale Bluetooth a bassa potenza. Il supporto dei beacon verrà rilasciato in una versione futura.

* Una **libreria** è una raccolta di POI, raggruppati per associare facilmente le regole a un set invece di un POI.

* Un’ **estensione** è l’estensione Experience Platform Launch necessaria per integrare l’SDK Places nelle app mobili.

   L’estensione utilizzata con gli altri SDK per dispositivi mobili per aggiungere contesto di posizione alle esperienze.

* Un’**organizzazione** è l’entità Adobe che identifica la società dell’utente in Adobe Experience Cloud.

   In genere, un'organizzazione è il vostro nome società. Tuttavia, un'azienda può avere più di un'organizzazione. L’amministratore dell’organizzazione può configurare gruppi e utenti e configurare la funzionalità di Single Sign-On.

* L’**orgID** è l’ID che rappresenta l’organizzazione dell’utente in Adobe Experience Platform.

   Per ulteriori informazioni, vedi [Ricerca del tuo orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).
