---
title: Creare più POI
seo-title: Creare più POI
description: Utilizzate le API batch per creare più POI.
seo-description: Utilizzate le API batch per creare più POI.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Creare più POI {#create-multiple-pois}

Metodo POST che consente di creare più POI.

## Richiesta

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate
```

## Intestazioni

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{    "createPOIRequests": [        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        .        .        .        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        }    ]}
```

## Risposta di esempio

```text
{    "ids": [        "558360b5-5b4b-4c8a-777f-5e3f4b60e4cb",        "ac01c21c-6274-4922-86d5-7777b59dc9b0",        .        .        .        "acf0fde0-22ee-470a-bfa9-b760777cefdc",        "d3cf8338-520f-49a5-8ee7-3777df69be91"    ],    "_links": {        "pois": {            "href": "https://api-places-dev.adobe.io/places/placesapi/v1/pois/{poi_id}",            "templated": true        }    }}
```

## CURL, comando

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHCREATEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituisci `<API KEY>`, `<TOKEN>`, `<ORGID>`e `<PATHTOBATCHCREATEJSONFILE>` con valori reali.

## Esempio di file JSON

Ecco il file JSON di esempio per l' `batchCreate` API:

```text
{    "createPOIRequests": [{            "name": "Sample POI 1",            "description": "1",            "location": {                "type": "Point",                "coordinates": [0.0, 0.0]            },            "radius": 25,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "red",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 2",            "description": "2",            "location": {                "type": "Point",                "coordinates": [0.025, 0.025]            },            "radius": 50,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "blue",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 3",            "description": "3",            "location": {                "type": "Point",                "coordinates": [0.05, 0.05]            },            "radius": 100,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "green",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        }    ]}
```