---
title: Ottenere il rango di una biblioteca
seo-title: Ottenere il rango di una biblioteca
description: Ottenete il rango di una libreria utilizzando l'API REST di Places.
seo-description: Ottenete il rango di una libreria utilizzando l'API REST di Places.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Ottenere il rango di una biblioteca

Un metodo GET che consente di classificare le librerie.

## Richiesta

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Intestazioni

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Risposta di esempio

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL, comando

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Sostituire variabili quali `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

