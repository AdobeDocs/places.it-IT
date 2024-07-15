---
title: Panoramica
description: Informazioni e utilizzo delle API Query.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%

---

# API di query

Metodo di GET che consente di eseguire query sui punti di interesse più vicini al chiamante.

## Richiesta

```text
GET https://query.places.adobe.com/placesedgequery
```

Con il seguente input, il servizio restituisce un elenco dei POI più vicini al chiamante:

* Posizione del chiamante (latitudine, longitudine).
* Gli ID delle librerie POI da includere nella ricerca.
* Il numero massimo di POI da restituire.  Il valore predefinito è 100.

  La distanza tra il chiamante e il punto di interesse (POI) è definita come la distanza tra il chiamante e il bordo del recinto geografico del POI. Nella risposta, i POI che contengono il chiamante saranno contrassegnati come aventi il chiamante.

Gli argomenti vengono forniti come i seguenti parametri di query:

* (**Obbligatorio**) `latitude`

  La latitudine del chiamante, che deve essere compresa tra -85 e 85.
* (**Obbligatorio**) `longitude`

  La longitudine del chiamante, che deve essere compresa tra -180 e 180.

* (**Facoltativo**) `limit`

  Il numero massimo di POI da restituire.

* (**Obbligatorio**) `library`

  ID della libreria su cui eseguire la query. Per eseguire query su più librerie, accertati di includere più copie del parametro libreria nella query.

Ecco un esempio del formato JSON restituito correttamente:

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

I POI sotto `places.pois` sono ordinati in base alla distanza dal chiamante al bordo dei POI. I POI sotto `places.userWithin` contengono il chiamante e questi POI sono ordinati per rango e poi per raggio crescente.

## Chiamata di esempio

Ecco un esempio della chiamata:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
