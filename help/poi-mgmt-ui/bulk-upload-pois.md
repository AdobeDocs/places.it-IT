---
title: POI di caricamento in blocco
description: Questa sezione fornisce informazioni su come caricare in massa i POI.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Caricamento in blocco di POI {#bulk-upload-pois}

È stato creato un set di script Python per semplificare l’importazione batch di POI da un file .csv in un database POI utilizzando le API dei servizi Web. Questi script possono essere scaricati da questo [git repo](https://github.com/adobe/places-scripts)open source.

Prima di eseguire questi script, per accedere alle API dei servizi Web, vedere *Prerequisiti per l'accesso* dell'utente in Panoramica dell' [integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

Seguono alcune informazioni sugli script:

>[!TIP]
>
>Queste informazioni sono incluse anche in un file Leggimi nel [git repo](https://github.com/adobe/places-scripts).

## file .CSV

Un file .csv di esempio `places_sample.csv`è parte del pacchetto e include le intestazioni richieste e una riga di dati di esempio. Queste intestazioni sono tutte minuscole e corrispondono alle chiavi di metadati riservate utilizzate nel database Places. Le colonne aggiunte al file .csv verranno aggiunte al database POI in una sezione di metadati separata per ciascun POI come coppie chiave/valore e il valore dell’intestazione viene utilizzato come chiave.

Elenco delle colonne e dei valori da utilizzare:

* `lib_id`

   Un ID libreria valido ottenuto dal database POI.

* `type`

   Il punto è attualmente l'unico valore valido.

* `longitude`

   Un valore compreso tra -180 e 180.

* `latitude`

   Un valore compreso tra -85 e 85.

* `radius`

   Un valore compreso tra 10 e 20.000.

### Valori colonna

I valori delle colonne seguenti vengono utilizzati nell’interfaccia utente del servizio di localizzazione:

* color, usato come colore del pin che rappresenta la posizione del POI nella mappa dell’interfaccia utente del servizio di posizione.
   * I valori validi sono "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B e #3DC8DE e "".
   * Se il valore viene lasciato vuoto, l’interfaccia utente del servizio posizione utilizza il blu come colore predefinito.

      I valori corrispondono a blu (#3E76D0), viola (#AA99E8), fuschia (#DC2ABA), arancione (#FC685B), arancione chiaro (#FC962E), giallo (#F6C436), verde chiaro (#BECE5D), verde (#61B 56B) e blu chiaro (#3DC8DE), rispettivamente.

* , che viene utilizzata come icona sul perno che rappresenta la posizione del POI sulla mappa dell’interfaccia utente del servizio di posizione

   * I valori validi sono "", negozio, alberghiero, auto, aeroplano, treno, nave, stadio, amusementpark, ancora, beaker, campana, bid, libro, box, valigetta, briefcase, browsing, pennello, edificio, calcolatore, macchina, orologio, istruzione, torcia, follow, gioco, femmina, maschio, regalo, martello, cuore, casa, chiave, lancio, lampadario, cassetta postale, promozionale, promozionale, nastro, shoppingCart, stella, target, teiera, thumbDown, thumbUp, trap, trofeo, chiave inglese.

      I valori delle icone sono elencati nell'ordine in cui appaiono nell'illustrazione seguente:

      ![icone nell’interfaccia](/help/assets/UI_icons.png)

   * Se il valore viene lasciato vuoto, l’interfaccia utente utilizza star come icona predefinita.

* Le colonne non menzionate possono essere lasciate vuote.

## Esecuzione dello script

1. Scaricate i file dal [git repo](https://github.com/adobe/places-scripts) nella directory locale.
1. In un editor di testo, aprite il `config.py` file e completate le seguenti operazioni:

   a. Modificate i seguenti valori di variabile come stringhe:

   * `csv_file_path`

      Percorso del `.csv` file.

   * `access_code`

      Questo è il codice di accesso ottenuto dalla chiamata ad Adobe IMS. Per informazioni su come ottenere questo codice di accesso, consultate *Prerequisiti per l'accesso* utente in Panoramica dell' [integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      ID organizzazione Experience Cloud in cui importare i POI. Per informazioni su come ottenere l’ID organizzazione, consultate *Prerequisiti per l’accesso* utente in Panoramica dell’ [integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Si tratta della chiave API REST di Places ottenuta dall'integrazione Adobe I/O Places. Per informazioni su come ottenere la chiave API, consultate *Prerequisiti per l'accesso* utente in Panoramica dell' [integrazione e prerequisiti](/help/web-service-api/adobe-i-o-integration.md).
   b.Salvare le modifiche.

1. In una finestra terminale, andate alla `…/places-scripts/import/` directory.
1. Inserite `python ./places_import.py` e premete il **[!UICONTROL enter]** (**[!UICONTROL return]**) tasto.


## Controlli CSV pre-importazione

Lo script completa inizialmente i seguenti controlli sul file .csv:

* Specifica se è stato specificato un `.csv` file.
* Se il percorso del file è valido.
* Indica se le intestazioni di metadati riservate sono incluse.

   Le intestazioni di metadati riservate sono lib_id, nome, descrizione, tipo, longitudine, latitudine, raggio, paese, stato, città, strada, categoria, icona e colore.

   >[!TIP]
   >
   >Le intestazioni sono tutte in lettere maiuscole e possono essere elencate in qualsiasi ordine.

* Verifica i valori delle colonne specificate nella sezione del file CSV.

Se vengono rilevati errori, lo script stampa gli errori e viene interrotto. Se non viene rilevato alcun errore, lo script tenta di importare i POI in batch di 1000. Se il batch viene importato correttamente, lo script segnala un codice di stato pari a 200. Se il batch non viene importato correttamente, vengono riportati gli errori.

## Prove di unità

I test di unità si trovano nel `tests.py` file, devono essere eseguiti prima di ogni richiesta di pull e devono essere tutti superati. È necessario aggiungere altri test con un nuovo codice. Per eseguire i test, andate alla `…/places-scripts/import/` directory e immettete `python ./places_import.py` nel terminale.
