---
title: Crea un POI
seo-title: Crea un POI
description: Create un POI utilizzando le API REST di Luoghi.
seo-description: Create un POI utilizzando le API REST di Luoghi.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Crea un POI

Metodo POST che consente di creare un POI.

## Richiesta

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois
```

## Intestazioni

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Corpo

```text
{
  "name": "string",
  "description": "string",
  "location": {
    "type": Point",
    "coordinates": [<LONGITUDE>, <LATITUDE>]
  },
  "radius": radius,
  "country": "string",
  "state": "string",
  "city": "string",
  "street": "string",
  "category": "string",
  "icon": "string",
  "color": "string",
  "metadata": {
          "brand": "string",
          "owndership": "string",
          "Color": "string"
  },
  "lib_id": "{libraryID}"
}
```

## Risposta di esempio

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",
    "name": "New POI",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -123.000507,
            37.698029
        ]
    },
    "radius": 66,
    "country": "US",
    "state": "CA",
    "city": "Small City",
    "street": "1 Island Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Island station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## CURL, comando

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Ricorda di sostituire `<API KEY>`, `<TOKEN>`, ',' e `<SINGLEPOIDATA>` con valori effettivi.
