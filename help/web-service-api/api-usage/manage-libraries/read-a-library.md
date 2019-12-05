---
title: Lettura di una libreria
description: Leggete una libreria utilizzando l'API REST di Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---



# Lettura di una libreria

Un metodo GET che restituisce i dettagli di una libreria.

## Richiesta

```text
GET https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>
```

## Intestazioni

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Risposta di esempio

```text
{
    "id": "9aa7f663-35cc-4de6-8643-ae7779f3bb87",
    "name": "Facinating places",
    "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",
    "poiCount": 30,
    "metadataDescriptors": [
        {
            "key": "region",
            "type": "string",
            "value": "Equator",
            "count": 29
        },
        {
            "key": "ownership",
            "type": "string",
            "value": "LS",
            "count": 1
        },
        {
            "key": "brand",
            "type": "string",
            "value": "Coffee Cafe",
            "count": 1
        },
        {
            "key": "Color",
            "type": "string",
            "value": "Blue",
            "count": 1
        }
    ],
    "poiCountInCities": [
        {
            "country": "Ghana",
            "state": "Ghana",
            "city": "Accra",
            "count": 29
        },
        {
            "country": "CN",
            "state": "91",
            "city": "Hong Kong",
            "count": 1
        }
    ]
}
```

## CURL, comando

Utilizzate il seguente comando CURL per testare l'API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Sostituisci `<LIBRARYID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

