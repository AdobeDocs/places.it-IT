---
title: Definire gli elementi dati
description: Questa sezione fornisce informazioni su come creare, utilizzare e pubblicare elementi dati in Experienci Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Definire un elemento dati {#define-data-elements}

Le informazioni seguenti sono utili per comprendere gli elementi dati e come crearli e pubblicarli.

## Informazioni sugli elementi dati

Gli elementi dati sono gli elementi costitutivi del dizionario dati dell’applicazione e vengono utilizzati per raccogliere, organizzare e inviare dati per le tecnologie di marketing e annunci.

Un elemento dati è una variabile in cui il valore può essere mappato a un ID visitatore, a un Nome gestore, a un ID Advertising, a un ID push e così via. In Experience Platform Launch, puoi fare riferimento a questo valore per mezzo del suo nome variabile. Questa raccolta di elementi dati diventa il dizionario di dati definiti che puoi utilizzare per creare le tue regole (eventi, condizioni e azioni) e questo dizionario viene condiviso in tutto il Experience Platform Launch, dove può essere utilizzato con qualsiasi estensione nella tua proprietà.

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


## Elementi dati di Publish

Se gli elementi dati vengono utilizzati in uno qualsiasi dei componenti della regola, anche questi devono essere inclusi nella libreria e pubblicati.
