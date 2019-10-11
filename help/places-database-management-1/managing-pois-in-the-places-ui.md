---
title: Gestire i POI nell’interfaccia utente Luoghi
seo-title: Gestire i POI nell’interfaccia utente Luoghi
description: Usate l’interfaccia utente Luoghi per gestire i POI.
seo-description: Usate l’interfaccia utente Luoghi per gestire i POI.
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Gestire i POI nell’interfaccia utente Luoghi

I POI e le librerie vengono creati e gestiti nel database Luoghi utilizzando l’interfaccia utente Luoghi.

## Definizione di un POI geografico

Le geofence sono un tipo di POI e sono definite nel database in base alle seguenti chiavi:

| Chiavi | Descrizione | Obbligatorio? |
| :--- | :--- | :--- |
| ID | Identificatore univoco assegnato a ciascun POI | Sì |
| Nome | Nome descrittivo assegnato al POI | Sì |
| Libreria | A ciascun POI deve essere assegnata una libreria per l’organizzazione | Sì |
| Icona | Assistenza nelle visualizzazioni dei POI | Yes (predefinito assegnato) |
| Colore | Assistenza nelle visualizzazioni dei POI | Yes (predefinito assegnato) |
| Categoria | Assegnazione di un framework comune di categorie comuni a tutti i POI di tutte le librerie | No |
| Indirizzo | Indirizzo via | No |
| Città | città di POI | No |
| Stato/Regione | stato o regione del POI | No |
| Paese | paese dell'area di interesse | No |
| Latitudine | Coordinata Latitude per il centro del POI | Sì |
| Longitudine | Coordinata longitudine per il centro del POI | Sì |
| Metadati | coppie chiave-valore personalizzate che possono essere assegnate ai punti di interesse. Questi metadati semplificano i flussi di lavoro futuri consentendo di raggruppare i POI tra le librerie in modo che ciascuno possa utilizzare regole e filtri nei flussi di lavoro a valle, ad esempio inviare una notifica push ogni volta che un utente accede a un POI con Tipo = Concorrente. | No |

## Crea un POI {#create-a-poi}

Un punto di interesse (POI) è una posizione o un punto di una mappa che ti interessa. Può includere luoghi come caffè, ristoranti e così via.

1. Accedi ad Adobe Places con il tuo Adobe ID.
2. In alto a destra, fate clic sull’icona che ha l’aspetto di un elenco puntato e fate clic **[!UICONTROL New]**.
3. Digitate un nome per il POI.
4. Selezionate o aggiungete una libreria.
5. Immettere o selezionare un raggio.

   a. Selezionate un’icona per il POI.
b.b. Selezionare un colore per l'icona.

6. Espandi la **[!UICONTROL Location]** sezione.

   a. Digitate un indirizzo.

   b. Digita la città.

   c. Digitare il nome dello stato.

   d. Digitare il nome del paese.

   e. Selezionare o immettere una latitudine o una longitudine.

   f.Fate clic **[!UICONTROL Drop Pin on Map]**.

7. Espandete la **[!UICONTROL Metadata]** sezione e fate clic su **[!UICONTROL Add Metadata]**.

   a. Digitate il nome della chiave.

   b. Digitare il valore della chiave.

8. Fare clic **[!UICONTROL Confirm]** e quindi **[!UICONTROL  Save]**.

## Modificare un POI

1. Accedi a Luoghi utilizzando il tuo Adobe ID.
1. Accedi ad Adobe Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fate clic sull’icona che ha l’aspetto di un elenco puntato.
1. Individuate il POI da modificare.
1. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL View Details]**.
1. Aggiornate le informazioni e fate clic **[!UICONTROL Save]**.

## Eliminare un POI

1. Accedi a Luoghi utilizzando il tuo Adobe ID.
1. Accedi ad Adobe Places Service utilizzando il tuo Adobe ID.
1. In alto a destra, fate clic sull’icona che ha l’aspetto di un elenco puntato.
1. Individuate il POI da eliminare.
1. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL Delete]**.

## Filtrare i POI per città, stato, Paese o metadati

1. Accedi ad Adobe Places Service utilizzando il tuo Adobe ID.
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

