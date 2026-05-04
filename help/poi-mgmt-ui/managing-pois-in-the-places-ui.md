---
title: Gestisci punti di interesse esistenti
description: Nell’interfaccia utente di Places Service puoi modificare, eliminare o filtrare i punti di interesse esistenti.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# Gestisci punti di interesse esistenti {#managing-existing-pois}

I POI e le librerie vengono creati e gestiti nel database Places utilizzando l’interfaccia utente di Places.

## Modificare un POI

1. Accedi a Places utilizzando il tuo Adobe ID.
1. Accedi a Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona che sembra un elenco puntato.
1. Individua il POI da modificare.
1. Fare clic su **[!UICONTROL ...]** e selezionare **[!UICONTROL Visualizza dettagli]**.
1. Aggiorna le informazioni e fai clic su **[!UICONTROL Salva]**.

## Eliminare un POI

1. Accedi a Places utilizzando il tuo Adobe ID.
1. Accedi a Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona che sembra un elenco puntato.
1. Individua il POI da eliminare.
1. Fai clic su **[!UICONTROL ...]** e seleziona **[!UICONTROL Elimina]**.

## Filtrare i punti di interesse per città, stato, paese o metadati

![filtrare un POI](/help/assets/filter_poi.png)

1. Accedi all’interfaccia utente di Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona del filtro.
1. Puoi filtrare i POI in uno dei seguenti modi:

   * Per libreria:

     a. Seleziona una libreria.

   * Per proprietà:

     a. Nell&#39;elenco a discesa Proprietà selezionare **[!UICONTROL Paese]**, **[!UICONTROL Stato]** o **[!UICONTROL Città]**.

     b. Nella riga successiva, immetti un valore.

     Ad esempio, puoi selezionare **[!UICONTROL Stato]** e digitare **[!UICONTROL California]**.

   * Con metadati:

     a. Immetti una chiave e un valore.

## Definizione di un punto di interesse del recinto geografico

I recinti geografici sono un tipo di POI e sono definiti nel database in base alle seguenti chiavi:

| Chiavi | Descrizione | Obbligatorio |
| :--- | :--- | :--- |
| ID | Identificatore univoco assegnato a ciascun POI | Sì |
| Nome | Nome intuitivo assegnato al punto di interesse. | Sì |
| Libreria | A ogni punto di interesse deve essere assegnata una libreria per l’organizzazione. | Sì |
| Raggio | Raggio del punto di interesse (POI) in metri. | Sì |
| Icona | Fornisce assistenza per le visualizzazioni dei punti di interesse. | Sì (impostazione predefinita assegnata) |
| Colore | Fornisce assistenza per le visualizzazioni dei punti di interesse. | Sì (impostazione predefinita assegnata) |
| Categoria | Assegna un framework comune di categorie comuni a tutti i POI in tutte le librerie. | No |
| Indirizzo | Indirizzo. | No |
| Città | Città del POI. | No |
| Stato/Regione | Stato o regione del punto di interesse (POI). | No |
| Paese | Paese del POI. | No |
| Latitudine | Coordinata della latitudine per il centro del punto di interesse (POI). | Sì |
| Longitudine | Coordinata longitudine per il centro del punto di interesse (POI). | Sì |
| Metadati | Coppie chiave-valore personalizzate che possono essere assegnate ai POI. Questi metadati semplificano i flussi di lavoro futuri consentendo di raggruppare i punti di interesse tra librerie per ciascuna di esse in modo da utilizzare regole e filtri nei flussi di lavoro a valle, ad esempio inviare una notifica push quando qualcuno entra in un punto di interesse con Tipo = Concorrente. | No |
