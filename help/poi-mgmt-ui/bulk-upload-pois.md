---
title: POI di caricamento in blocco
seo-title: POI di caricamento in blocco
description: Questa sezione fornisce informazioni su come caricare in massa i POI.
seo-description: Questa sezione fornisce informazioni su come caricare in massa i POI.
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Caricamento in blocco di POI {#bulk-upload-pois}

È stato creato un set di script Python per semplificare l’importazione batch di POI da un file .csv in un database POI utilizzando le API dei servizi Web. Questi script possono essere scaricati da questo [git repo](https://github.com/adobe/places-scripts)open source.

Prima di eseguire questi script, per essere certi di avere accesso alle API dei servizi Web, vedere *Prerequisiti per l'accesso* utente nella panoramica [dell'integrazione di I/O di](/help/web-service-api/adobe-i-o-integration.md)Adobe.

Seguono alcune informazioni sugli script:

>[!TIP]
>
>Queste informazioni sono incluse anche in un file Leggimi nel [git repo](https://github.com/adobe/places-scripts).

## file .CSV

Un file .csv di esempio `places_sample.csv`è parte del pacchetto e include le intestazioni richieste e una riga di dati di esempio. Queste intestazioni sono tutte minuscole e corrispondono alle chiavi di metadati riservate utilizzate nel database Places. Quando aggiungete intestazioni, le colonne aggiuntive vengono aggiunte al database POI in una sezione di metadati separata per ciascun POI come coppie chiave/valore.

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

   Un valore compreso tra 10 e 2000.

### Valori colonna

I valori delle colonne seguenti vengono utilizzati nell’interfaccia utente del servizio di localizzazione:

* color, usato come colore del pin che rappresenta la posizione del POI nella mappa dell’interfaccia utente del servizio di posizione.
   * I valori validi sono "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B e #3DC8DE.
   * Se il valore viene lasciato vuoto, l’interfaccia utente del servizio posizione utilizza il blu come colore predefinito.

      I valori corrispondono rispettivamente a blu, viola, fuschia, arancione, arancione chiaro, giallo, verde chiaro, verde e blu chiaro.

* che viene utilizzata come icona sul perno che rappresenta la posizione del POI sulla mappa dell’interfaccia utente del servizio di posizione
   * I valori validi sono "", ancora, becher, campana, navigare, libro, pennello, edificio, macchina fotografica, shoppingCart, orologio, scatola, torcia, follow, bid, ribbon, istruzione, martello, cuore, a casa, chiave, cassetta postale, maschio, promuovere, soldi, trappola, gioco, lancio, stella, lampadina, pin, target, teiera, thumbDown, thumbUp valigetta, trofeo, femmina e chiave inglese.
   * Se il valore viene lasciato vuoto, l’interfaccia utente utilizza star come icona predefinita.

* Le colonne non menzionate possono essere lasciate vuote.

## Esecuzione dello script

1. Scaricate i file nella directory appropriata.
1. In un editor di testo, aprite il `config.py` file e completate le seguenti operazioni:

   a. Modificate i seguenti valori di variabile come stringhe:

   * `csv_file_path`

      Percorso del `.csv` file.

   * `access_code`

      Questo è il codice di accesso ottenuto dalla chiamata ad Adobe IMS.

   * `org_id`

      ID organizzazione Experience Cloud in cui importare i POI.

   * `api_key`

      Si tratta della chiave API REST di Places ottenuta dall'integrazione Adobe I/O Places.
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



