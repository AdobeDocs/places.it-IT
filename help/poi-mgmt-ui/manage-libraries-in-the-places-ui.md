---
title: Gestione delle librerie nell'interfaccia utente del servizio Luoghi
description: Gestire le librerie utilizzando l'interfaccia utente del servizio Luoghi.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Manage libraries {#manage-libraries-places-ui}

Una libreria è una raccolta di POI. Puoi avere fino a 150.000 POI in una libreria e fino a 100 librerie per organizzazione Experience Cloud.

Esistono diversi modi per organizzare i POI in librerie, a seconda di cosa sia più utile per l’organizzazione. Alcuni clienti potrebbero preferire creare una libreria separata per ciascuna app mobile, mentre altri potrebbero utilizzare le librerie per raggruppare tipi specifici di POI, ad esempio caffetterie, parchi, hotel e così via. Ad esempio, una grande azienda di intrattenimento potrebbe avere una libreria che comprende i suoi locali all&#39;aperto in una libreria e i suoi negozi al dettaglio in un&#39;altra libreria. Un governo della città potrebbe avere una biblioteca che comprende tutti gli edifici della città e un&#39;altra biblioteca che comprende tutti i parchi della città.

Le librerie sono definite dalle seguenti:

| Chiavi: | Descrizione: |
| :--- | :--- |
| ID | un identificatore univoco assegnato alla libreria al momento della creazione |
| Nome | un nome descrittivo assegnato a una libreria |
| Preferenza | Queste classificazioni possono essere ignorate se nell’organizzazione non sono presenti aree geografiche sovrapposte. In presenza di punti di interesse sovrapposti, consigliamo di inserire ciascuno dei recinti geografici in librerie separate, in modo che possano essere ponderati gli uni rispetto gli altri. Un utente può trovarsi in un solo recinto geografico alla volta. <br><br>La classificazione più alta dei recinti geografici in cui si trova un utente determina la sua attuale appartenenza al recinto geografico. Se esistono aree geografiche con la stessa classificazione della libreria, la distanza minima è quella corrente dell&#39;utente. <br><br>L’SDK riconosce inoltre i punti di interesse *Last entered* (Ultimo in entrata) e *Last exited* (Ultimo in uscita), per cui hai il controllo completo sulle modalità con cui attivare le regole in base all’interazione dell’utente con i punti di interesse. |

## Creare una libreria

1. Accedi a Luoghi con il tuo Adobe ID.
1. In alto a destra, fate clic su **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Fai clic su **[!UICONTROL New]**.
1. Digitate il nome.
1. Fai clic su **[!UICONTROL Confirm]**.

## Modificare il livello di una libreria nell’interfaccia utente Luoghi

1. Accedi a Luoghi con il tuo Adobe ID.
1. In alto a destra, fate clic su **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Fate clic sull&#39;icona a sinistra del nome della libreria e trascinatela nella nuova posizione.

## Rinominare una libreria

1. Accedi a Luoghi con il tuo Adobe ID.
1. In alto a destra, fate clic su **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Individuate la libreria da eliminare.
1. Fate clic **[!UICONTROL ...]**e selezionate**[!UICONTROL Rename]**.
1. Aggiorna il nome e fai clic su **[!UICONTROL Save]**.

## Eliminare una libreria

1. Accedi a Luoghi con il tuo Adobe ID.
1. In alto a destra, fate clic su **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Individuate la libreria da eliminare.
1. Fate clic **[!UICONTROL ...]**e selezionate**[!UICONTROL Delete]**.

