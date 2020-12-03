---
title: Eliminare un POI
description: Eliminate un POI utilizzando le API REST Luoghi.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 2%

---


# Eliminare un POI {#delete-a-poi}

Un metodo DELETE che consente di eliminare un POI.

## Richiesta

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
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
If successful a Status of "204 No Content" is returned.
```

## CURL, comando

Utilizzate il seguente comando CURL per testare l&#39;API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Sostituisci `<POIID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

