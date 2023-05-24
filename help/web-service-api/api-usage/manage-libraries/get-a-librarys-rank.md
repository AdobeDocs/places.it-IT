---
title: Ottieni il rango di una libreria
description: Ottieni il rango di una libreria utilizzando l’API REST Places.
exl-id: c0abedd0-5ff4-4a01-9f8d-e3d17ea53a97
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 9%

---

# Ottieni il rango di una libreria {#get-library-rank}

Metodo di GET che consente di classificare le librerie.

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
>Sostituisci variabili come `<API KEY>`, `<TOKEN>`, e `<ORGID>` con i valori effettivi.
