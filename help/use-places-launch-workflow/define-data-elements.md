---
title: Definire gli elementi dati
description: Questa sezione fornisce informazioni su come creare, utilizzare e pubblicare elementi dati in Experience Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 1%

---

# Definire un elemento dati {#define-data-elements}

Le informazioni seguenti sono utili per comprendere gli elementi dati e come crearli e pubblicarli.

## Informazioni sugli elementi dati

Gli elementi dati sono gli elementi costitutivi del dizionario dati dell’applicazione e vengono utilizzati per raccogliere, organizzare e inviare dati per le tecnologie di marketing e annunci.

Un elemento dati è una variabile in cui il valore può essere mappato a un ID visitatore, a un Nome gestore, a un ID Advertising, a un ID push e così via. In Experience Platform Launch, puoi fare riferimento a questo valore per mezzo del suo nome variabile. Questa raccolta di elementi dati diventa il dizionario di dati definiti che è possibile utilizzare per creare le regole (eventi, condizioni e azioni) e questo dizionario viene condiviso in Experience Platform Launch, dove può essere utilizzato con qualsiasi estensione della proprietà.

Con l’estensione Luoghi, puoi fare riferimento ai valori delle seguenti destinazioni:

* POI corrente, che si riferisce al POI in cui il cliente si trova attualmente.

  Se l’utente si trova in più punti di interesse, viene scelto quello che appartiene alla libreria con un livello più alto. Se più punti di interesse appartengono alla libreria di classificazione più alta, viene scelto quello con il raggio più basso.
* Last exited POI (Ultimo punto di interesse in uscita), che si riferisce al punto di interesse più recente chiuso dall&#39;utente.
* Last entered POI (Ultimo POI inserito), che si riferisce al POI più recente inserito dall’utente.

Ogni POI contiene i seguenti riferimenti dati:

* **[!UICONTROL Categoria]**: categoria del POI
* **[!UICONTROL Città]**: città del POI
* **[!UICONTROL Paese]**: paese del POI
* **[!UICONTROL Latitudine]**: latitudine del punto di interesse
* **[!UICONTROL Longitudine]**: longitudine del punto di interesse
* **[!UICONTROL Metadati]**: metadati personalizzati del punto di interesse
* **[!UICONTROL Nome]**: nome del punto di interesse
* **[!UICONTROL Raggio]**: raggio del punto di interesse
* **[!UICONTROL ID area geografica]**: ID del punto di interesse (POI)
* **[!UICONTROL Regione/Stato]**: area geografica, provincia o stato del POI

### Creare un elemento dati

1. Nella pagina Proprietà dell&#39;app, fai clic sulla scheda **[!UICONTROL Elementi dati]**.

1. Fai clic su **[!UICONTROL Crea nuovo elemento dati]**.

1. Nell&#39;elenco delle estensioni installate, trovare **[!UICONTROL Places]**.

1. Nell&#39;elenco a discesa **[!UICONTROL Tipo di elemento dati]** selezionare un riferimento ai dati per questo elemento dati.

1. Seleziona una destinazione POI.

1. Se questo elemento dati è un riferimento di metadati personalizzato, seleziona una chiave di metadati.

1. Digitare un nome per l&#39;elemento dati e fare clic su **[!UICONTROL Salva]**.

   ![Crea elemento dati](/help/assets/create-de-7-v3.png)


## Utilizzare un elemento dati

Dopo la creazione di un elemento dati, se è presente un selettore di elementi dati, puoi utilizzare l’elemento dati da qualsiasi componente regola.

![Utilizza l&#39;elemento dati](/help/assets/use-de-v2.png)

Se nel componente regola non è presente un selettore di elementi dati, è possibile utilizzare l&#39;elemento dati racchiudendo il nome dell&#39;elemento dati con i token **[!UICONTROL %]**.
Ad esempio, se il nome dell&#39;elemento dati è **[!UICONTROL Last POI City]**, puoi aggiungere **[!UICONTROL LAST POI City]** a un input di testo.


## Pubblicare elementi dati

Se gli elementi dati vengono utilizzati in uno qualsiasi dei componenti della regola, anche questi devono essere inclusi nella libreria e pubblicati.
