---
title: Aggiornare un POI
description: Aggiorna un POI utilizzando le API REST Places.
exl-id: f155d1d3-88a3-47bc-bffe-a35842a639e2
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 6%

---

# Aggiornare un POI {#update-a-poi}

Metodo PUT che consente di aggiornare un POI.

## Richiesta

```text
PUT https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Intestazioni

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{  "id": "string",  "name": "string",  "description": "string",  "location": {    "type": Point",    "coordinates": [<LONGITUDE>, <LATITUDE>]  },  "radius": 0,  "country": "string",  "state": "string",  "city": "string",  "street": "string",  "category": "string",  "icon": "string",  "color": "string",  "metadata": {          "brand": "string",          "owndership": "string"          },  "lib_id": "{libraryID}"}
```

## Risposta di esempio

```text
{    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",    "name": "New Name",    "description": "18827",    "location": {        "type": "Point",        "coordinates": [            -123.000507,            37.698029        ]    },    "radius": 66,    "country": "US",    "state": "CA",    "city": "Small City",    "street": "1 Island Road",    "category": "",    "icon": "",    "color": "",    "metadata": {        "ownership": "LS",        "brand": "Island station"    },    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"}
```

## CURL, comando

Utilizza il seguente comando CURL per testare questa API:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituisci `<POIID>`, `<API KEY>`, `<TOKEN>`, `<ORGID>` e `<SINGLEPOIDATA>` con i valori effettivi.
