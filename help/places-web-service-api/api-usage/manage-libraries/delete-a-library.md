---
title: Eliminare una libreria
seo-title: Eliminare una libreria
description: Eliminate una libreria utilizzando le API REST Luoghi.
seo-description: Eliminate una libreria utilizzando le API REST Luoghi.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# Eliminare una libreria

Un metodo DELETE che consente di eliminare una libreria.

## Richiesta

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Sostituire variabili quali `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>`con valori effettivi.
