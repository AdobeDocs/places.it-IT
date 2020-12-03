---
title: Utilizzo dei metadati con i POI
description: Questa sezione fornisce informazioni e strategie sull’utilizzo dei metadati con i POI.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Strategie per utilizzare i metadati con i POI {#using-metadata-pois}

Nel servizio Luoghi, quando create un nuovo POI, gli unici elementi richiesti sono Nome, Raggio, Latitudine e Longitudine. Per ulteriori informazioni sulla creazione di un POI, consultate [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Tuttavia, se state solo inserendo le informazioni minime, non avrete la possibilità di creare valore aggiuntivo.

I metadati POI possono essere utilizzati in diversi modi. Dal punto di vista della gestione dei POI, l’aggiunta di valori di metadati può essere utile per cercare o filtrare un elenco di migliaia di POI potenzialmente disponibili. La creazione di metadati per gli attributi chiave relativi a un POI può dare valore ai flussi di lavoro a valle. Ad esempio, una catena alberghiera che crea punti di interesse per ogni proprietà potrebbe includere metadati, ad esempio se la struttura dell&#39;hotel dispone di una piscina o meno, oppure un ristorante e un bar, o se dispongono di una struttura in palestra. Questi metadati possono essere inclusi come dati contestuali nell&#39;analisi e possono essere utilizzati anche per offerte o messaggi mirati.

## Metadati del servizio Luoghi in Launch

Ad Experience Platform Launch, puoi creare elementi di dati per ciascun campo di metadati Servizio Luoghi che è importante ai fini del tracciamento o della messaggistica.

![elemento dati per la struttura della palestra](/help/assets/gymfacility.png)

Puoi quindi creare un’azione con l’estensione Analytics per creare un nuovo hit che includa i metadati desiderati come dati contestuali.

![azione per la palestra](/help/assets/Analytics-gym.png)

## Messaggistica in-app in  Adobe Campaign

I metadati possono essere utilizzati come filtro per le notifiche locali e i messaggi in-app definiti in  Adobe Campaign Standard. L&#39;utilizzo dei metadati come filtro consente di creare un messaggio più rilevante, contestuale alla posizione effettiva.

![filtro delle notifiche locali e dei messaggi in-app in ACS](/help/assets/ACS_gym_metadata.png)