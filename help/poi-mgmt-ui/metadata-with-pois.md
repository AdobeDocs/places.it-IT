---
title: Utilizzo dei metadati con i POI
description: Questa sezione fornisce informazioni e strategie sull’utilizzo dei metadati con i POI.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 0%

---

# Strategie per l’utilizzo dei metadati con i punti di interesse {#using-metadata-pois}

In Places Service, quando crei un nuovo POI, gli unici elementi richiesti sono Nome, Raggio, Latitudine e Longitudine. Per ulteriori informazioni sulla creazione di un punto di interesse, vedi [Creare un punto di interesse](/help/poi-mgmt-ui/create-a-poi-ui.md). Tuttavia, se si immettono solo le informazioni minime, si perderà l&#39;opportunità di creare valore aggiuntivo.

I metadati dei punti di interesse possono essere utilizzati in diversi modi. Dal punto di vista della gestione dei punti di interesse, l’aggiunta di valori di metadati può essere utile per cercare o filtrare un elenco di potenziali migliaia di punti di interesse. La creazione di metadati per gli attributi chiave correlati a un POI può produrre valore nei flussi di lavoro a valle. Ad esempio, una catena di hotel che crea punti di interesse per ogni proprietà potrebbe voler includere metadati come se la proprietà dell’hotel avesse o meno una piscina, un ristorante e un bar, o se avesse una struttura per palestra. Questi metadati possono essere inclusi come dati contestuali in Analytics e possono essere utilizzati anche per offerte mirate o messaggi.

## Metadati di Places Service in Launch

In Experience Platform Launch, puoi creare elementi dati per ogni campo di metadati di Places Service importante a scopo di tracciamento o messaggistica.

![elemento dati per la struttura della palestra](/help/assets/gymfacility.png)

Con l’estensione Analytics puoi quindi creare un’azione per creare un nuovo hit che includa tutti i metadati desiderati come dati contestuali.

![azione per la struttura della palestra](/help/assets/Analytics-gym.png)

## Messaggistica in-app in Adobe Campaign

I metadati possono essere utilizzati come filtro per le notifiche locali e i messaggi in-app definiti in Adobe Campaign Standard. L’utilizzo dei metadati come filtro offre l’opportunità di creare un messaggio più rilevante e contestuale rispetto alla posizione effettiva.

![filtraggio di notifiche locali e messaggi in-app in ACS](/help/assets/ACS_gym_metadata.png)
