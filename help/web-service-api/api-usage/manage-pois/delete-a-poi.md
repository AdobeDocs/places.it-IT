---
title: Eliminare un POI
seo-title: Eliminare un POI
description: Eliminate un POI utilizzando le API REST Luoghi.
seo-description: Eliminate un POI utilizzando le API REST Luoghi.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Eliminare un POI

Metodo DELETE che consente di eliminare un POI.

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

Utilizzate il seguente comando CURL per testare l'API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Sostituisci `<POIID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.
