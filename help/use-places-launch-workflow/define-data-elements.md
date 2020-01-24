---
title: Definizione degli elementi di dati
description: Questa sezione fornisce informazioni su come creare, utilizzare e pubblicare elementi di dati in Experience Platform Launch for Places.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# Define a data element {#define-data-elements}

Le seguenti informazioni sono utili per comprendere gli elementi di dati e come crearli e pubblicarli.

## Informazioni sugli elementi dati

Gli elementi dati sono gli elementi costitutivi del dizionario dati dell&#39;applicazione e sono utilizzati per raccogliere, organizzare e distribuire dati attraverso marketing e tecnologie pubblicitarie.

Un elemento dati è una variabile in cui il valore può essere mappato su un ID visitatore, un Nome gestore, un ID pubblicitario, un ID push e così via. In Experience Platform Launch puoi fare riferimento a questo valore in base al nome della variabile. Questa raccolta di elementi di dati diventa il dizionario di dati definiti che puoi utilizzare per creare le tue regole (eventi, condizioni e azioni) e questo dizionario è condiviso tra Experience Platform Launch, dove può essere utilizzato con qualsiasi estensione nella tua proprietà.

Con l&#39;estensione Luoghi, potete fare riferimento ai valori delle seguenti destinazioni:

* POI correnti, che si riferisce al POI in cui il cliente si trova attualmente.

   Se l’utente si trova in più POI, viene scelto quello che appartiene alla libreria con un livello superiore. Se più POI appartengono alla libreria con rango più alto, viene scelto quello con il raggio più piccolo.
* Ultimo POI uscito, che fa riferimento al POI più recente uscito dall’utente.
* Ultimo POI immesso, che fa riferimento al POI più recente immesso dall’utente.

Ciascun POI contiene i seguenti riferimenti di dati:

* **[!UICONTROL Category]**: categoria di POI
* **[!UICONTROL City]**: città del POI
* **[!UICONTROL Country]**: paese dell’API
* **[!UICONTROL Latitude]**: latitudine del POI
* **[!UICONTROL Longitude]**: longitudine del POI
* **[!UICONTROL Metadata]**: metadati personalizzati del POI
* **[!UICONTROL Name]**: nome del POI
* **[!UICONTROL Radius]**: raggio del POI
* **[!UICONTROL Region ID]**: ID del POI
* **[!UICONTROL Region/State]**: regione, provincia o stato dell&#39;OPA

### Creare un elemento dati

1. Nella pagina Proprietà dell&#39;app, fai clic sulla **[!UICONTROL Data Elements]**scheda.

1. Fai clic su **[!UICONTROL Create New Data Element]**.

1. Nell&#39;elenco delle estensioni installate, trovate **[!UICONTROL Places]**.

1. Nell&#39;elenco a **[!UICONTROL Data Element Type]**discesa, selezionare un riferimento dati per questo elemento dati.

1. Selezionate una destinazione POI.

1. Se questo elemento dati è un riferimento di metadati personalizzato, selezionate una chiave di metadati.

1. Digitare un nome per l&#39;elemento dati e fare clic **[!UICONTROL Save]**.

   ![Crea elemento dati](/help/assets/create-de-7-v3.png)


## Uso di un elemento dati

Dopo la creazione di un elemento dati, se è presente un selettore di elementi dati, puoi utilizzare l&#39;elemento dati da qualsiasi componente regola.

![Utilizzare l&#39;elemento dati](/help/assets/use-de-v2.png)

Se nel componente regola non è presente un selettore di elementi di dati, potete utilizzare l&#39;elemento di dati racchiudendo il nome dell&#39;elemento di dati con i **[!UICONTROL %%]**token.
Ad esempio, se il nome dell&#39;elemento dati è**[!UICONTROL Last POI City]**, è possibile aggiungere **[!UICONTROL LAST POI City]**a un input di testo.


## Pubblicare gli elementi di dati

Se gli elementi dati sono utilizzati in uno qualsiasi dei componenti regola, questi devono essere inclusi nella libreria e pubblicati.
