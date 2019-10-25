---
title: 'Panoramica API dei servizi Web '
seo-title: 'Panoramica API dei servizi Web '
description: Luoghi è l'insieme di servizi che semplifica l'idratazione da parte dei clienti Adobe delle soluzioni Adobe Experience Cloud e Adobe Experience Platform con i dati sulla posizione e l'esperienza giusta per la persona giusta al momento giusto e nel posto giusto.
seo-description: Luoghi è l'insieme di servizi che semplifica l'idratazione da parte dei clienti Adobe delle soluzioni Adobe Experience Cloud e Adobe Experience Platform con i dati sulla posizione e l'esperienza giusta per la persona giusta al momento giusto e nel posto giusto.
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Panoramica API dei servizi Web {#places-web-services-api}

Luoghi è l'insieme di servizi che semplifica l'idratazione da parte dei clienti Adobe delle soluzioni Adobe Cloud Platform e Adobe Experience Platform con i dati sulla posizione e l'esperienza giusta per la persona giusta al momento giusto e nel posto giusto.

Le API dei servizi Web consentono di effettuare le seguenti operazioni:

* Gestire le aree sicure
* Misurare la posizione degli utenti anche quando l'app è in background
* Usa i dati in tempo reale quando sono importanti

Questa sezione fornisce informazioni sull’utilizzo delle API REST e del database POI, che contiene i dati POI della tua organizzazione.

## API REST

L’API REST Luoghi consente di lavorare in modo programmatico con i POI dell’organizzazione. Queste API consentono di creare, aggiornare ed eliminare le librerie e i POI in tali librerie. Queste API utilizzano gli standard JavaScript Object Notation (JSON) per formattare i dati inviati e ricevuti. Un vantaggio principale di JSON è che rende le query API facili da scrivere, leggere e analizzare da sviluppatori e computer.

Prima di poter utilizzare l'API dei servizi Web, accertati che siano stati soddisfatti i seguenti requisiti:

* Il provisioning dei luoghi avviene all'interno dell'organizzazione e l'utente dispone dell'accesso appropriato come utente.

   Per ulteriori informazioni, consulta la sezione *Requisiti* di organizzazione di seguito.

* Dopo che il provisioning di Places è stato eseguito nell’organizzazione e l’utente dispone dell’accesso, create un’integrazione Adobe per Places.

   Per ulteriori informazioni, consultate *Creazione dell'integrazione* Luoghi nella panoramica [dell'integrazione di](/help/web-service-api/adobe-i-o-integration.md)Adobe I/O.

Informazioni aggiuntive:

* Per ulteriori informazioni sulle API disponibili e su come utilizzarle, consultate [Gestire le librerie](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gestire i POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Per ulteriori informazioni sulle intestazioni e i parametri di queste API, consultate [Intestazioni e parametri](/help/web-service-api/api-usage/headers-and-parameters.md).

## Requisiti organizzativi {#org-requirements}

Per accedere alle API REST dei servizi Web, verifica con l’amministratore di sistema che le seguenti attività siano state completate:

* I luoghi sono stati predisposti e sono visualizzati nell'organizzazione.
* È stato aggiunto all'organizzazione.
* Sei stato aggiunto a Places nella tua organizzazione.

   Per ulteriori informazioni, consulta *Aggiunta di un utente a Luoghi e al lancio* della piattaforma di esperienze in [Domande](/help/places-faqs.md)frequenti.

* È stato aggiunto come sviluppatore Luoghi alla propria organizzazione.

   Per ulteriori informazioni sul ruolo di sviluppatore, consultate [Gestire gli sviluppatori](https://helpx.adobe.com/enterprise/using/manage-developers.html).