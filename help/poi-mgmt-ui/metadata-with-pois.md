---
title: Utilizzo dei metadati con i POI
seo-title: Utilizzo dei metadati con i POI
description: Questa sezione fornisce informazioni e strategie sull’utilizzo dei metadati con i POI.
seo-description: 'Questa sezione fornisce informazioni e strategie sull’utilizzo dei metadati con i POI. '
translation-type: tm+mt
source-git-commit: 6a01c7c2c573baf572fdc27f47f8fc62322cfd02

---


# Strategie per utilizzare i metadati con i POI {#using-metadata-pois}

In Location Service, quando create un nuovo POI, gli unici elementi richiesti sono Nome, Raggio, Latitudine e Longitudine. Per ulteriori informazioni sulla creazione di un POI, consultate [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Tuttavia, se state solo inserendo le informazioni minime, non avrete la possibilità di creare valore aggiuntivo.

I metadati dei punti di interesse possono essere utilizzati in diversi modi. Dal punto di vista della gestione dei POI, l’aggiunta di valori di metadati può facilitare la ricerca o il filtraggio di un elenco di migliaia di POI potenzialmente disponibili. La creazione di metadati per gli attributi chiave relativi a un POI può dare valore ai flussi di lavoro a valle. Ad esempio, una catena alberghiera che crea punti di interesse per ogni proprietà potrebbe includere metadati, ad esempio se la struttura dell'hotel dispone di una piscina o meno, oppure un ristorante e un bar, o se dispongono di una struttura in palestra. Questi metadati possono essere inclusi come dati contestuali nell'analisi e possono essere utilizzati anche per offerte o messaggi mirati.

## Metadati di Location Service in Launch

In Adobe Experience Platform Launch puoi creare elementi di dati per ogni campo di metadati Location Service, importanti a scopo di tracciamento o messaggistica.

![elemento dati per la struttura della palestra](/help/assets/gymfacility.png)

Puoi quindi creare un’azione con l’estensione Analytics per creare un nuovo hit che includa i metadati desiderati come dati contestuali.

![azione per la palestra](/help/assets/Analytics-gym.png)

## Messaggistica in-app in Adobe Campaign

I metadati possono essere utilizzati come filtro per le notifiche locali e i messaggi in-app definiti in Adobe Campaign Standard. L'utilizzo dei metadati come filtro consente di creare un messaggio più rilevante, contestuale alla posizione effettiva.

![filtro delle notifiche locali e dei messaggi in-app in ACS](/help/assets/ACS_gym_metadata.png)