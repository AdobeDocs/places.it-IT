---
title: Eliminare un POI
seo-title: Eliminare un POI
description: Eliminate un POI utilizzando le API REST Luoghi.
seo-description: Eliminate un POI utilizzando le API REST Luoghi.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

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

