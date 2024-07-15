---
title: Gestire le librerie nell’interfaccia utente di Places Service
description: Gestisci le librerie utilizzando l’interfaccia utente di Places Service.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 14%

---

# Gestione librerie {#manage-libraries-places-ui}

Una libreria è una raccolta di POI. In una libreria possono essere presenti fino a 150.000 punti di interesse e fino a 100 librerie per organizzazione di Experience Cloud.

Esistono diversi modi per organizzare i punti di interesse in librerie, a seconda di ciò che è più utile per la tua organizzazione. Alcuni clienti preferiscono creare una libreria separata per ogni app mobile, mentre altri possono utilizzare le librerie per raggruppare tipi specifici di POI, ad esempio coffee shop, parchi, hotel e così via. Ad esempio, una grande azienda di intrattenimento potrebbe avere una libreria che comprende i locali all&#39;aperto in una libreria e i negozi al dettaglio in un&#39;altra libreria. Un&#39;amministrazione comunale potrebbe avere una biblioteca che comprende tutti gli edifici della città e un&#39;altra biblioteca che comprende tutti i parchi della città.

Le librerie sono definite dai seguenti elementi:

| Chiavi: | Descrizione: |
| :--- | :--- |
| ID | un identificatore univoco assegnato alla libreria al momento della creazione |
| Nome | un nome descrittivo assegnato a una libreria |
| Classifica | Queste classificazioni possono essere ignorate se nell’organizzazione non sono presenti recinti geografici sovrapposti. In presenza di punti di interesse sovrapposti, consigliamo di inserire ciascuno dei recinti geografici in librerie separate, in modo che possano essere ponderati gli uni rispetto gli altri. Un utente può trovarsi in un solo recinto geografico alla volta. <br><br>La classificazione più alta dei recinti geografici in cui si trova un utente determina la sua attuale appartenenza al recinto geografico. Se ci sono recinti geografici con la stessa classificazione della libreria, quello minore è il recinto geografico corrente dell’utente. <br><br>L&#39;SDK è inoltre a conoscenza dei punti di interesse *Last entered* e *Last exited*, pertanto hai il controllo completo sulle modalità con cui attivare le regole in base all&#39;interazione dell&#39;utente con i punti di interesse. |

## Creare una libreria

1. Accedi a Places con il tuo Adobe ID.
1. In alto a destra, fai clic su **[!UICONTROL ...]** > **[!UICONTROL Gestisci librerie]**.
1. Fai clic su **[!UICONTROL Nuovo]**.
1. Digita il nome.
1. Fai clic su **[!UICONTROL Conferma]**.

## Modificare la classificazione di una libreria nell’interfaccia utente Luoghi

1. Accedi a Places con il tuo Adobe ID.
1. In alto a destra, fai clic su **[!UICONTROL ...]** > **[!UICONTROL Gestisci librerie]**.
1. Fai clic sull’icona a sinistra del nome della libreria e trascina la libreria nella nuova classificazione.

## Rinominare una libreria

1. Accedi a Places con il tuo Adobe ID.
1. In alto a destra, fai clic su **[!UICONTROL ...]** > **[!UICONTROL Gestisci librerie]**.
1. Individua la libreria da eliminare.
1. Fare clic su **[!UICONTROL ...]** e selezionare **[!UICONTROL Rinomina]**.
1. Aggiorna il nome e fai clic su **[!UICONTROL Salva]**.

## Eliminare una libreria

1. Accedi a Places con il tuo Adobe ID.
1. In alto a destra, fai clic su **[!UICONTROL ...]** > **[!UICONTROL Gestisci librerie]**.
1. Individua la libreria da eliminare.
1. Fai clic su **[!UICONTROL ...]** e seleziona **[!UICONTROL Elimina]**.
