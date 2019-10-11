---
title: Impostare un livello nelle librerie
seo-title: Impostare un livello nelle librerie
description: Impostate una classificazione nelle librerie utilizzando l'API REST Luoghi.
seo-description: Impostate una classificazione nelle librerie utilizzando l'API REST Luoghi.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Impostare un livello nelle librerie

Metodo PUT che consente di impostare un ordine di classificazione per tutte le librerie.

## Richiesta

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## Intestazioni

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Dati PUT

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## Risposta di esempio

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURL, comando

```
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Sostituire variabili quali `<API KEY>`, `<TOKEN>`e `<ORGID>` con valori effettivi.

