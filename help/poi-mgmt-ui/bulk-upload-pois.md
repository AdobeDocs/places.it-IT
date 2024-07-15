---
title: POI di caricamento in blocco
description: Questa sezione fornisce informazioni su come caricare in blocco i POI.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Caricamento in blocco di POI {#bulk-upload-pois}

Il pulsante **Importa POI** nel servizio Places può essere utilizzato per caricare in blocco nuovi POI utilizzando un file CSV. Viene fornito un modello di foglio di calcolo di esempio per mostrare quali colonne di dati sono necessarie e come aggiungere metadati personalizzati facoltativi.

![Schermata di importazione in blocco](/help/assets/Bulk-import.png)

Guarda questo video che mostra il processo di importazione e modifica in blocco:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importazione in blocco di Places Service e modifica POI](https://www.youtube.com/watch?v=75qVtirsXhg)

## Script API Python

È stato creato un set di script Python per semplificare l’importazione batch di POI da un file .csv a un database POI utilizzando le API dei servizi Web. Questi script possono essere scaricati da questo archivio Git [open source](https://github.com/adobe/places-scripts).

Prima di eseguire questi script, per accedere alle API dei servizi Web, vedere *Prerequisiti per l&#39;accesso utente* in [Panoramica dell&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

Seguono alcune informazioni sugli script:

>[!TIP]
>
>Queste informazioni sono incluse anche in un file readme nell&#39;archivio [Git](https://github.com/adobe/places-scripts).

## File CSV

Un file .csv di esempio, `places_sample.csv`, fa parte di questo pacchetto e include le intestazioni richieste e una riga di dati di esempio. Queste intestazioni sono tutte minuscole e corrispondono alle chiavi di metadati riservate utilizzate nel database Places. Le colonne aggiunte al file .csv verranno aggiunte al database POI in una sezione di metadati separata per ciascun POI come coppie chiave/valore e il valore dell’intestazione viene utilizzato come chiave.

Elenco delle colonne e dei valori da utilizzare:

* `lib_id`

  Un ID libreria valido ottenuto dal database POI.

* `type`

  Punto è attualmente l&#39;unico valore valido.

* `longitude`

  Un valore compreso tra -180 e 180.

* `latitude`

  Un valore compreso tra -85 e 85.

* `radius`

  Un valore compreso tra 10 e 20.000.

### Valori colonna

Nell’interfaccia utente di Places Service vengono utilizzati i valori delle seguenti colonne:

* color, che viene utilizzato come colore del pin che rappresenta la posizione del POI nella mappa dell’interfaccia utente di Places Service.
   * I valori validi sono &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B e #3DC8DE e &quot;&quot;.
   * Se il valore viene lasciato vuoto, l’interfaccia utente di Places Service utilizza il blu come colore predefinito.

     I valori corrispondono rispettivamente a blu (#3E76D0), viola (#AA99E8), fuschia (#DC2ABA), arancione (#FC685B), arancione chiaro (#FC962E), giallo (#F6C436), verde chiaro (#BECE5D), verde (#61B56B) e blu chiaro (#3DC8DE).

* che viene utilizzata come icona sul pin che rappresenta la posizione del POI sulla mappa dell’interfaccia utente di Places Service.

   * I valori validi sono: &quot;&quot;, shop, hotelbed, car, airplane, train, ship, stadium, amusementpark, anchor, beaker, bell, bid, book, box, Sincronia file, browse, brush, building, calcolatrice, fotocamera, orologio, istruzione, torcia elettrica, follow, game, femmina, maschio, regalo, martello, cuore, casa, key, launch, lightbulb, mailbox, money, pin, promote, ribbon, shoppingCart, star, target, teiera, thumbDown, thumbUp, trap, trophy, wrench.

     I valori delle icone sono elencati nell&#39;ordine in cui compaiono nella figura seguente:

     ![icone nell&#39;interfaccia utente](/help/assets/UI_icons.png)

   * Se il valore viene lasciato vuoto, l’interfaccia utente utilizza l’icona stella come icona predefinita.

* Le colonne non menzionate possono essere lasciate vuote.

## Esecuzione dello script

1. Scarica i file dall&#39;[archivio Git](https://github.com/adobe/places-scripts) nella directory locale.
1. In un editor di testo, aprire il file `config.py` e completare le attività seguenti:

   a. Modifica i seguenti valori delle variabili come stringhe:

   * `csv_file_path`

     Percorso del file `.csv`.

   * `access_code`

     Questo è il codice di accesso ottenuto dalla chiamata ad Adobe IMS. Per informazioni su come ottenere questo codice di accesso, vedere *Prerequisiti per l&#39;accesso utente* in [Panoramica dell&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     L’orgID di Experience Cloud in cui i POI devono essere importati. Per informazioni su come ottenere l&#39;ID organizzazione, vedere *Prerequisiti per l&#39;accesso utente* in [Panoramica dell&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Questa è la chiave API REST di Places ottenuta dall’integrazione di Adobe I/O Places. Per informazioni su come ottenere la chiave API, vedere *Prerequisiti per l&#39;accesso utente* in [Panoramica dell&#39;integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

   b. Salva le modifiche.

1. In una finestra del terminale, passare alla directory `…/places-scripts/import/`.
1. Immetti `python ./places_import.py` e premi la chiave **[!UICONTROL enter]** (**[!UICONTROL return]**).


## Controlli CSV pre-importazione

Lo script esegue inizialmente i seguenti controlli sul file .csv:

* Specifica di un file `.csv`.
* Indica se il percorso del file è valido.
* Se sono incluse le intestazioni di metadati riservate.

  Le intestazioni di metadati riservate sono lib_id, name, description, type, longitude, latitude, radius, country, state, city, street, category, icon e color.

  >[!TIP]
  >
  >Le intestazioni sono tutte minuscole e possono essere elencate in qualsiasi ordine.

* Verifica i valori delle colonne specificate nella sezione del file CSV.

Se vengono rilevati errori, lo script stampa gli errori e viene interrotto. Se non vengono trovati errori, lo script tenta di importare i POI in batch di 1000. Se il batch viene importato correttamente, lo script riporta il codice di stato 200. Se il batch non viene importato correttamente, vengono segnalati errori.

## Test di unità

Gli unit test si trovano nel file `tests.py`, devono essere eseguiti prima di ogni richiesta di pull e devono essere tutti superati. È necessario aggiungere altri test con un nuovo codice. Per eseguire i test, passare alla directory `…/places-scripts/import/` e immettere `python ./places_import.py` nel terminale.
