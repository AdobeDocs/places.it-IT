---
title: Gestire le librerie nell’interfaccia utente di Places Service
description: Gestisci le librerie utilizzando l’interfaccia utente di Places Service.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# Gestione librerie {#manage-libraries-places-ui}

Una libreria è una raccolta di POI. In una libreria possono essere presenti fino a 150.000 punti di interesse e fino a 100 librerie per organizzazione Experience Cloud.

Esistono diversi modi per organizzare i punti di interesse in librerie, a seconda di ciò che è più utile per la tua organizzazione. Alcuni clienti preferiscono creare una libreria separata per ogni app mobile, mentre altri possono utilizzare le librerie per raggruppare tipi specifici di POI, ad esempio coffee shop, parchi, hotel e così via. Ad esempio, una grande azienda di intrattenimento potrebbe avere una libreria che comprende i locali all&#39;aperto in una libreria e i negozi al dettaglio in un&#39;altra libreria. Un&#39;amministrazione comunale potrebbe avere una biblioteca che comprende tutti gli edifici della città e un&#39;altra biblioteca che comprende tutti i parchi della città.

Le librerie sono definite dai seguenti elementi:

| Chiavi: | Descrizione: |
| :--- | :--- |
| ID | un identificatore univoco assegnato alla libreria al momento della creazione |
| Nome | un nome descrittivo assegnato a una libreria |
| Ranking | Queste classificazioni possono essere ignorate se nell’organizzazione non sono presenti recinti geografici sovrapposti. In presenza di punti di interesse sovrapposti, consigliamo di inserire ciascuno dei recinti geografici in librerie separate, in modo che possano essere ponderati gli uni rispetto gli altri. Un utente può trovarsi in un solo recinto geografico alla volta. <br><br>La classificazione di geofencing più alta in cui si trova un utente determina l’appartenenza al geofence attuale. Se ci sono recinti geografici con la stessa classificazione della libreria, quello minore è il recinto geografico corrente dell’utente. <br><br>SDK è inoltre a conoscenza dei punti di interesse *Last entered* e *Last exited*, pertanto hai il controllo completo sulle modalità con cui attivare le regole in base all&#39;interazione dell&#39;utente con i punti di interesse. |

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
