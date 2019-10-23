---
title: Gestione delle librerie nell'interfaccia utente Luoghi
seo-title: Gestione delle librerie nell'interfaccia utente Luoghi
description: Gestire le librerie utilizzando l'interfaccia utente Luoghi.
seo-description: Gestire le librerie utilizzando l'interfaccia utente Luoghi.
translation-type: tm+mt
source-git-commit: fdfeb8c17820c4eb0eae249da39be4eebece22d3

---


# Gestione delle librerie nell'interfaccia utente Luoghi {#manage-libraries-places-ui}

Una libreria è una raccolta di POI. Puoi avere fino a 150.000 POI in una libreria e fino a 100 librerie per organizzazione Experience Cloud.

Esistono diversi modi per organizzare i POI in librerie, a seconda di cosa sia più utile per l’organizzazione. Alcuni clienti potrebbero preferire creare una libreria separata per ciascuna app mobile, mentre altri potrebbero utilizzare le librerie per raggruppare tipi specifici di POI, ad esempio caffetterie, parchi, hotel e così via. Ad esempio, una grande azienda di intrattenimento potrebbe avere una libreria che comprende i suoi locali all'aperto in una libreria e i suoi negozi al dettaglio in un'altra libreria. Un governo della città potrebbe avere una biblioteca che comprende tutti gli edifici della città e un'altra biblioteca che comprende tutti i parchi della città.

Le librerie sono definite dalle seguenti:

| Chiavi: | Descrizione: |
| :--- | :--- |
| ID | un identificatore univoco assegnato alla libreria al momento della creazione |
| Nome | un nome descrittivo assegnato a una libreria |
| Preferenza | Queste classificazioni possono essere ignorate se nell’organizzazione non sono presenti aree geografiche sovrapposte. In presenza di punti di interesse sovrapposti, si consiglia di inserire ciascuna delle aree geografiche in librerie separate, in modo che possano essere ponderate l’una rispetto all’altra. Un utente può trovarsi in una sola area geografica alla volta. <br><br>La classificazione più alta delle aree sicure in cui si trova un utente determina la sua attuale appartenenza alle aree geografiche. In presenza di aree geografiche con la stessa classificazione della libreria, la distanza minima è rappresentata dalla distanza corrente dell'utente. <br><br>L’SDK è inoltre a conoscenza dei punti di interesse *Ultimo entrato* e *Ultimo uscito* , per cui hai il controllo completo su come vuoi che vengano attivate le regole in base all’interazione dell’utente con i punti di interesse. |

## Creare una libreria

1. Accedi ad Adobe Places con il tuo Adobe ID.
2. In alto a destra, fate clic su **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Fai clic su **[!UICONTROL New]**.
4. Digitate il nome.
5. Fai clic su **[!UICONTROL Confirm]**.

## Modificare il livello di una libreria nell’interfaccia utente Luoghi

1. Accedi ad Adobe Places con il tuo Adobe ID.
2. In alto a destra, fate clic su **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Fate clic sull'icona a sinistra del nome della libreria e trascinatela nella nuova posizione.

## Rinominare una libreria

1. Accedi ad Adobe Places con il tuo Adobe ID.
2. In alto a destra, fate clic su **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Individuate la libreria da eliminare.
4. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL Rename]**.
5. Aggiorna il nome e fai clic su **[!UICONTROL Save]**.

## Eliminare una libreria

1. Accedi ad Adobe Places con il tuo Adobe ID.
2. In alto a destra, fate clic su **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Individuate la libreria da eliminare.
4. Fate clic **[!UICONTROL ...]** e selezionate **[!UICONTROL Delete]**.
