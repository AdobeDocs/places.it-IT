---
title: Panoramica dell’API dei servizi Web
description: Places Service è l’insieme di servizi che semplificano, ad Adobe, l’idratazione delle soluzioni Adobe Experience Cloud e Adobe Experience Platform con i dati sulla posizione e l’esperienza giusta per la persona giusta al momento giusto e nel posto giusto.
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Panoramica API dei servizi Web {#places-web-services-api}

Places Service è l’insieme di servizi che semplificano, ad Adobe, l’idratazione delle soluzioni Adobe Cloud Platform e Adobe Experience Platform con i dati sulla posizione e l’esperienza giusta per la persona giusta al momento giusto e nel posto giusto.

Le API dei servizi web consentono di effettuare le seguenti operazioni:

* Gestire i recinti geografici
* Misura la posizione degli utenti anche quando l’app è in background
* Utilizzare i dati in tempo reale quando è importante

Questa sezione fornisce informazioni su come utilizzare le API REST e il database POI, che contiene i dati POI dell&#39;organizzazione.

## API REST

L’API REST di Places Service consente di lavorare in modo programmatico con i POI dell’organizzazione. Queste API ti consentono di creare, aggiornare ed eliminare le librerie e i POI in esse contenuti. Queste API utilizzano gli standard JSON (JavaScript Object Notation) per formattare i dati inviati e ricevuti. Uno dei principali vantaggi di JSON è la facilità con cui le query API vengono scritte, lette e analizzate da sviluppatori e computer.

Prima di poter utilizzare l’API dei servizi web, assicurati di aver soddisfatto i seguenti requisiti:

* Il provisioning di Places Service viene eseguito nell’organizzazione e l’utente dispone dell’accesso appropriato.

  Per ulteriori informazioni, vedere *Prerequisiti per l&#39;accesso utente* in [Panoramica sull&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

* Dopo aver eseguito il provisioning di Places Service nell’organizzazione e aver effettuato l’accesso, crea un’integrazione di Adobe per Places Service.

  Per ulteriori informazioni, vedere *Creazione di un&#39;integrazione di Places Service* in [Panoramica sull&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

Informazioni aggiuntive:

* Per ulteriori informazioni sulle API disponibili e su come utilizzarle, vedi [Gestione librerie](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gestione POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Per ulteriori informazioni sulle intestazioni e i parametri di queste API, vedi [Intestazioni e parametri](/help/web-service-api/api-usage/headers-and-parameters.md).
