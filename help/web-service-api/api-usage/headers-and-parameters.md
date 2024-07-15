---
title: Intestazioni e parametri
description: Intestazioni e parametri disponibili nelle API REST di Places Service.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# Intestazioni e parametri {#headers-and-parameters}

Di seguito sono riportati i dettagli relativi alle intestazioni e ai parametri disponibili nell’API REST di Places Service:

## Intestazioni supportate

| Header | Descrizione | Metodo | Esempio |
| :--- | :--- | :--- | :--- |
| `Authorization` | Token bearer | Tutto |  |
| `x-api-key` | Chiave API | Tutto | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | ID organizzazione | Tutto | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato del contenuto inviato o ricevuto | PUT, POST | `application/json` |
| `Accept-Language` | Lingua utilizzata per i messaggi di errore | Facoltativo | `en-US` |

## Parametri libreria

| Parametro | Descrizione | Tipo | Limite | Richiesta o risposta | Esempio |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID libreria | assegnato | n/d | Risposta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nome della libreria | stringa | 256 caratteri | entrambi, obbligatorio nella richiesta | `"name": "Amazing Places"` |
| `orgID` | ID organizzazione Experience Cloud dell’organizzazione | assegnato | n/d | Risposta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Numero di POI nella libreria | intero | massimo 150.000 | Risposta | `"poiCount": 25149` |
| `metadataDescriptors` | Conteggio per ogni coppia di valori chiave di metadati POI univoci | misto | n/d | Risposta |  |
| `poiCountInCities` | Conteggio per ogni valore univoco della città POI | misto | n/d | Risposta |  |

## Parametri POI

| Parametro | Descrizione | Tipo | Limite | Richiesta o risposta | Esempio |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Dati POI | Array di dettagli POI | n/d | entrambi |  |
| `id` | ID del punto di interesse | assegnato | n/d | risposta | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nome del punto di interesse | stringa | 512 caratteri | entrambi, facoltativo\* | `"name": "My Favorite Place"` |
| `description` | Descrizione del punto di interesse | stringa | 512 caratteri | entrambi, facoltativo\* | `"description": "This is a very good place."` |
| `location` | Array del tipo e coordinate di POI | array (misto) | n/d | entrambi | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo di POI | stringa | attualmente supportato solo &quot;Point&quot; | entrambi, obbligatorio nella richiesta | `"type": "Point"` |
| `coordinates` | Array di longitudine e latitudine del punto di interesse (POI) | array (in virgola mobile) | longitudine: da -180 a 180, latitudine da -85 a 85 | entrambi, obbligatorio nella richiesta | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Dimensione del recinto geografico circolare attorno al punto di interesse (POI) | mobile | 10 - 2000 metri | entrambi, obbligatorio nella richiesta | `"radius": 100` |
| `country` | Paese per il POI | stringa | 32 caratteri | entrambi, opzionali* | `"country": "United States"` |
| `state` | Stato del POI | stringa | 32 caratteri | entrambi, opzionali* | `"state": "California"` |
| `city` | Città per il POI | stringa | 32 caratteri | entrambi, opzionali* | `"city": "San Jose"` |
| `street` | Indirizzo del POI | stringa | 256 caratteri | entrambi, opzionali* | `"street": "122 Woz Way"` |
| `category` | Categoria per il POI | stringa | 100 caratteri | entrambi, opzionali* | `"category": "cafe"` |
| `icon` | Icona per il punto di interesse | stringa | 50 caratteri | entrambi, opzionali* | `"icon": "star"` |
| `color` | Colore per il punto di interesse | stringa | 8 caratteri | entrambi, opzionali* | `"color": "blue"` |
| `metadata` | Array di coppie chiave/valore per il POI | array(string) | chiave: 256 caratteri, valore: 256 caratteri, massimo 10 coppie | entrambi, opzionali* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID della libreria in cui si trova il punto di interesse | n/d | n/d | entrambi, obbligatorio | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Se il valore del parametro non è incluso, il valore viene impostato su `empty` nel database. Se la coppia chiave/valore esistente non è inclusa, la coppia chiave/valore viene rimossa per quel POI nel database.
