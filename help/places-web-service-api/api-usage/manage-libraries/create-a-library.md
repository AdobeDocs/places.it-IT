---
title: Creare una libreria
seo-title: Creare una libreria
description: Create una libreria utilizzando l'API REST Luoghi.
seo-description: Create una libreria utilizzando l'API REST Luoghi.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# Creare una libreria

Un metodo POST che consente di creare una libreria.

## Richiesta

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Intestazioni

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{"name": "<LIBRARY_NAME>"}
```

## Risposta di esempio

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, comando

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituire variabili quali `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

