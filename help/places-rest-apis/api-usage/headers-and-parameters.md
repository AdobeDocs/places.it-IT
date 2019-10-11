---
title: Intestazioni e parametri
seo-title: Intestazioni e parametri
description: Intestazioni e parametri disponibili nelle API REST di Places.
seo-description: Intestazioni e parametri disponibili nelle API REST di Places.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Intestazioni e parametri {#headers-and-parameters}

Di seguito sono riportati i dettagli sulle intestazioni e i parametri disponibili nell'API REST di Places:

## Intestazioni supportate

| Intestazione | Descrizione | Metodo | Esempio |
| :--- | :--- | :--- | :--- |
| `Authorization` | Il tuo token | Tutte |  |
| `x-api-key` | La chiave API | Tutte | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Il tuo ID organizzazione | Tutte | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato del contenuto inviato o ricevuto | PUT, POST | `application/json` |
| `Accept-Language` | Lingua utilizzata per i messaggi di errore | Facoltativo | `en-US` |

## Parametri della libreria

| Parametro | Descrizione | Tipo | Limite | Richiesta o risposta | Esempio |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID della libreria | assegnato | n/d | Risposta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nome della libreria | string | 256 caratteri | entrambi, richiesti | `"name": "Amazing Places"` |
| `orgID` | Experience Cloud orgID dell'organizzazione | assegnato | n/d | Risposta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Numero di POI nella libreria | integer | 150.000 max | Risposta | `"poiCount": 25149` |
| `metadataDescriptors` | Conteggio per ogni coppia di valori chiave di metadati POI univoca | misto | n/d | Risposta |  |
| `poiCountInCities` | Conteggio per ogni valore di città POI univoco | misto | n/d | Risposta |  |

## Parametri POI

| Parametro | Descrizione | Tipo | Limite | Richiesta o risposta | Esempio |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Dati Poi | Matrice di dettagli POI | n/d | both |  |
| `id` | ID POI | assegnato | n/d | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nome del POI | string | 512 caratteri | both, optional\* | `"name": "My Favorite Place"` |
| `description` | Descrizione del POI | string | 512 caratteri | both, optional\* | `"description": "This is a very good place."` |
| `location` | Matrice di tipo e coordinate del POI | array (misto) | n/d | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo di POI | string | al momento è supportato solo "Point" | entrambi, richiesti | `"type": "Point"` |
| `coordinates` | Matrice di longitudine e latitudine del POI | array (mobile) | longitudine: Da -180 a 180, latitudine da -85 a 85 | entrambi, richiesti | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Dimensione del geofence circolare intorno al POI | float | 10 - 2000 metri | entrambi, richiesti | `"radius": 100` |
| `country` | Paese per POI | string | 32 caratteri | both, optional* | `"country": "United States"` |
| `state` | Stato per il POI | string | 32 caratteri | both, optional* | `"state": "California"` |
| `city` | Città per POI | string | 32 caratteri | both, optional* | `"city": "San Jose"` |
| `street` | Indirizzo della strada per il POI | string | 256 caratteri | both, optional* | `"street": "122 Woz Way"` |
| `category` | Categoria per POI | string | 100 caratteri | both, optional* | `"category": "cafe"` |
| `icon` | Icona per POI | string | 50 caratteri | both, optional* | `"icon": "star"` |
| `color` | Colore per POI | string | 8 caratteri | both, optional* | `"color": "blue"` |
| `metadata` | Matrice di coppie chiave/valore per il POI | array(string) | key: 256 caratteri, valore: 256 caratteri, massimo 10 coppie | both, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID della libreria in cui si trova il POI | n/d | n/d | entrambi, richiesti | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Se il valore del parametro non è incluso, il valore è impostato su `empty` nel database. Se la coppia chiave/valore esistente non è inclusa, la coppia chiave/valore viene rimossa per quel POI nel database.

