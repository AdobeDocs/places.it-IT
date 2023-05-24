---
title: Utilizzo dei metadati con i POI
description: Questa sezione fornisce informazioni e strategie sull’utilizzo dei metadati con i POI.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Strategie per l’utilizzo dei metadati con i punti di interesse {#using-metadata-pois}

In Places Service, quando crei un nuovo POI, gli unici elementi richiesti sono Nome, Raggio, Latitudine e Longitudine. Per ulteriori informazioni sulla creazione di un POI, vedi [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Tuttavia, se si immettono solo le informazioni minime, si perderà l&#39;opportunità di creare valore aggiuntivo.

I metadati dei punti di interesse possono essere utilizzati in diversi modi. Dal punto di vista della gestione dei punti di interesse, l’aggiunta di valori di metadati può essere utile per cercare o filtrare un elenco di potenziali migliaia di punti di interesse. La creazione di metadati per gli attributi chiave correlati a un POI può produrre valore nei flussi di lavoro a valle. Ad esempio, una catena di hotel che crea punti di interesse per ogni proprietà potrebbe voler includere metadati come se la proprietà dell’hotel avesse o meno una piscina, un ristorante e un bar, o se avesse una struttura per palestra. Questi metadati possono essere inclusi come dati contestuali in Analytics e possono essere utilizzati anche per offerte mirate o messaggi.

## Metadati di Places Service in Launch

In Experience Platform Launch, puoi creare elementi dati per ogni campo di metadati di Places Service importante a scopo di tracciamento o messaggistica.

![elemento dati per la struttura della palestra](/help/assets/gymfacility.png)

Con l’estensione Analytics puoi quindi creare un’azione per creare un nuovo hit che includa tutti i metadati desiderati come dati contestuali.

![azione per la palestra](/help/assets/Analytics-gym.png)

## Messaggistica in-app in Adobe Campaign

I metadati possono essere utilizzati come filtro per le notifiche locali e i messaggi in-app definiti in Adobe Campaign Standard. L’utilizzo dei metadati come filtro offre l’opportunità di creare un messaggio più rilevante e contestuale rispetto alla posizione effettiva.

![filtraggio delle notifiche locali e dei messaggi in-app in ACS](/help/assets/ACS_gym_metadata.png)
