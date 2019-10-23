---
title: Eliminare più POI
seo-title: Eliminare più POI
description: Usate le API batch per eliminare più POI.
seo-description: Usate le API batch per eliminare più POI.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# Eliminare più POI {#delete-multiple-pois}

Un metodo POST che consente di eliminare più POI.

## Richiesta

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Intestazioni

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Risposta di esempio

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, comando

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituisci `<API KEY>`, `<TOKEN>`, `<ORGID>`e `<PATHTOBATCHDELETEJSONFILE>` con valori reali.

## Esempio di file JSON

Ecco il file JSON di esempio per l' `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
