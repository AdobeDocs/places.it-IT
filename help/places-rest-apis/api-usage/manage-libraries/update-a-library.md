---
title: Aggiornare una libreria
seo-title: Aggiornare una libreria
description: Aggiornate una libreria utilizzando l'API REST Luoghi.
seo-description: Aggiornate una libreria utilizzando l'API REST Luoghi.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Aggiornare una libreria

Metodo PUT che consente di aggiornare una libreria.

## Richiesta

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## Intestazioni

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## Risposta di esempio

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, comando

Utilizzate il seguente comando CURL per testare questa API:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituire variabili quali `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

