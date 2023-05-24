---
title: Gestisci punti di interesse esistenti
description: Nell’interfaccia utente di Places Service puoi modificare, eliminare o filtrare i punti di interesse esistenti.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# Gestisci punti di interesse esistenti {#managing-existing-pois}

I POI e le librerie vengono creati e gestiti nel database Places utilizzando l’interfaccia utente di Places.

## Modificare un POI

1. Accedi a Places utilizzando il tuo Adobe ID.
1. Accedi a Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona che sembra un elenco puntato.
1. Individua il POI da modificare.
1. Clic **[!UICONTROL ...]** e seleziona **[!UICONTROL Visualizza dettagli]**.
1. Aggiorna le informazioni e fai clic su **[!UICONTROL Salva]**.

## Eliminare un POI

1. Accedi a Places utilizzando il tuo Adobe ID.
1. Accedi a Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona che sembra un elenco puntato.
1. Individua il POI da eliminare.
1. Clic **[!UICONTROL ...]** e seleziona **[!UICONTROL Elimina]**.

## Filtrare i punti di interesse per città, stato, paese o metadati

![filtrare un POI](/help/assets/filter_poi.png)

1. Accedi all’interfaccia utente di Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fai clic sull’icona del filtro.
1. Puoi filtrare i POI in uno dei seguenti modi:

   * Per libreria:

      a. Seleziona una libreria.

   * Per proprietà:

      a. Nell’elenco a discesa Proprietà, seleziona **[!UICONTROL Paese]**, **[!UICONTROL Stato]**, o **[!UICONTROL Città]**.

      b. Nella riga successiva, immettere un valore.

      Ad esempio, puoi selezionare **[!UICONTROL Stato]** e tipo **[!UICONTROL California]**.

   * Con metadati:

      a. Inserire una chiave e un valore.

## Definizione di un punto di interesse del recinto geografico

I recinti geografici sono un tipo di POI e sono definiti nel database in base alle seguenti chiavi:

| Chiavi | Descrizione | Obbligatorio? |
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
