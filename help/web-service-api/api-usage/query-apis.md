---
title: Panoramica
description: Informazioni e utilizzo delle API di query.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---



# API di query

Un metodo GET che consente di interrogare i POI più vicini al chiamante.

## Richiesta

```text
GET https://query.places.adobe.com/placesedgequery
```

Con il seguente input, il servizio restituisce un elenco dei POI più vicini al chiamante:

* Posizione del chiamante \(latitudine, longitudine\).
* ID delle librerie POI da includere nella ricerca.
* Il numero massimo di POI da restituire.  Il valore predefinito è 100.

   La distanza tra il chiamante e il POI è definita come la distanza tra il chiamante e il bordo della geofence del POI. Nella risposta, i POI che contengono il chiamante saranno contrassegnati come aventi il chiamante.

Gli argomenti vengono forniti come parametri di query seguenti:

* (**Obbligatorio**) `latitude`

   Latitudine del chiamante, che deve essere compresa tra -85 e 85.
* (**Obbligatorio**) `longitude`

   La longitudine del chiamante, che deve essere compresa tra -180 e 180.

* (**Facoltativo**) `limit`

   Il numero massimo di POI da restituire.

* (**Obbligatorio**) `library`

   ID della libreria da interrogare. Per eseguire query su più librerie, accertatevi di includere più copie del parametro della libreria nella query.

Di seguito è riportato un esempio del formato JSON restituito correttamente:

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

I POI sotto `places.pois` sono ordinati per distanza dal chiamante al bordo dei POI. I POI sotto `places.userWithin` contengono il chiamante, e questi POI sono ordinati per rango e poi per raggio crescente.

## Chiamata di esempio

Esempio di chiamata:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
