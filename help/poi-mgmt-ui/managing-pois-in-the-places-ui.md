---
title: Gestire i POI esistenti
seo-title: Gestire i POI esistenti
description: Nell’interfaccia utente del servizio di localizzazione potete modificare, eliminare o filtrare i POI esistenti.
seo-description: Nell’interfaccia utente del servizio di localizzazione potete modificare, eliminare o filtrare i POI esistenti.
translation-type: tm+mt
source-git-commit: 32c670773421406591ba85a628760553ce6ad840

---


# Gestire i POI esistenti

I POI e le librerie vengono creati e gestiti nel database Luoghi utilizzando l’interfaccia utente Luoghi.

## Modificare un POI

1. Accedi a Luoghi utilizzando il tuo Adobe ID.
1. Accedi al servizio Places utilizzando il tuo Adobe ID.
1. In alto a destra, fate clic sull’icona che ha l’aspetto di un elenco puntato.
1. Individuate il POI da modificare.
1. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL View Details]**.
1. Aggiornate le informazioni e fate clic **[!UICONTROL Save]**.

## Eliminare un POI

1. Accedi a Luoghi utilizzando il tuo Adobe ID.
1. Accedi al servizio Places utilizzando il tuo Adobe ID.
1. In alto a destra, fate clic sull’icona che ha l’aspetto di un elenco puntato.
1. Individuate il POI da eliminare.
1. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL Delete]**.

## Filtrare i POI per città, stato, Paese o metadati

![filtrare un POI](/help/assets/filter_poi.png)

1. Accedi all’interfaccia utente del servizio di localizzazione utilizzando il tuo Adobe ID.
1. In alto a destra, fate clic sull'icona di filtro.
1. Potete filtrare i POI in uno dei seguenti modi:

   * Per libreria:

      a. Selezionate una libreria.

   * Per proprietà:

      a. Nell'elenco a discesa Proprietà, selezionate **[!UICONTROL Country]**, **[!UICONTROL State]** o **[!UICONTROL City]**.

      b. Nella riga successiva, immettete un valore.

      Ad esempio, potete selezionare **[!UICONTROL State]** e digitare **[!UICONTROL California]**.

   * Con i metadati:

      a. Immettere una chiave e un valore.

## Definizione di un POI geografico

Le geofence sono un tipo di POI e sono definite nel database in base alle seguenti chiavi:

| Chiavi | Descrizione | Obbligatorio? |
| :--- | :--- | :--- |
| ID | Identificatore univoco assegnato a ciascun POI | Sì |
| Nome | Nome gentile dato al POI. | Sì |
| Libreria | A ciascun POI deve essere assegnata una libreria per l’organizzazione. | Sì |
| Icona | Assistenza nelle visualizzazioni dei punti di interesse. | Yes (predefinito assegnato) |
| Colore | Assistenza nelle visualizzazioni dei punti di interesse. | Yes (predefinito assegnato) |
| Categoria | Assegnate un framework comune di categorie comuni a tutti i POI di tutte le librerie. | No |
| Indirizzo | Indirizzo della strada. | No |
| Città | Città del POI. | No |
| Stato/Regione | Stato o regione del POI. | No |
| Paese | Paese del POI. | No |
| Latitudine | Coordinata latitudine per il centro del POI. | Sì |
| Longitudine | Coordinata della longitudine per il centro del POI. | Sì |
| Metadati | Coppie chiave e valore personalizzate che possono essere assegnate ai POI. Questi metadati semplificano i flussi di lavoro futuri consentendo di raggruppare i POI tra le librerie in modo che ciascuno possa utilizzare regole e filtri nei flussi di lavoro a valle, ad esempio inviare una notifica push quando un utente accede a un POI con Tipo = Concorrente. | No |
