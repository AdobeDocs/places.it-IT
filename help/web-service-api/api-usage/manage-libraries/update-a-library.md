---
title: Aggiornare una libreria
description: Aggiorna una libreria utilizzando l’API REST Places.
exl-id: 37ca2be2-39e1-4f8e-87c2-ef4cb366db0d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 10%

---

# Aggiornare una libreria {#update-a-library}

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

Utilizza il seguente comando CURL per testare questa API:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituisci variabili come `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`, e `<ORGID>` con i valori effettivi.
