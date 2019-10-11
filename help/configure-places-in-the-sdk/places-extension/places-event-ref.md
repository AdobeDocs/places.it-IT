---
title: Riferimento evento Luoghi
seo-title: Riferimento evento Luoghi
description: 'Un elenco degli eventi gestiti dall''estensione Luoghi. '
seo-description: 'Un elenco degli eventi gestiti dall''estensione Luoghi.  '
translation-type: tm+mt
source-git-commit: a785b75ccbed2a62d0e9f77b5c17dae9447b0629

---


# Riferimento evento Luoghi {#places-event-reference}

Elenco degli eventi gestiti dall'estensione Luoghi.

## GetCurrentPointsOfInterest

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| LUOGHI | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descrizione evento**

Questo evento è una richiesta per recuperare i POI in cui si trova il dispositivo.

**Definizione del carico utile dei dati**

n/d

## GetNearbyPointsOfInterest

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| LUOGHI | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Descrizione evento**

Questo evento è una richiesta per ottenere i POI vicini tenendo conto della posizione corrente del dispositivo e delle librerie Luoghi configurate.

**Definizione del carico utile dei dati**

| Chiave | Tipo di valore | Obbligatorio | Valore predefinito | Descrizione |
| :--- | :--- | :--- | :--- | :--- |
| latitudine | double | true | n/d | Contiene il valore di latitudine per il centro della ricerca di POI vicini. |
| longitudine | double | true | n/d | Contiene il valore di longitudine per il centro della ricerca di POI vicini. |
| radius | integer | false | n/d | Raggio, in metri, utilizzato dalla ricerca di POI vicini. |
| count | integer | false | 10 | Numero massimo di POI da restituire nell’evento di risposta risultante. |

## ProcessRegionEvent

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| LUOGHI | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Descrizione evento**

Questo evento causa l'elaborazione da parte dell'estensione Luoghi di un evento geofence entry o exit.

**Definizione del carico utile dei dati**

| Chiave | Tipo di valore | Obbligatorio | Descrizione |
| :--- | :--- | :--- | :--- |
| regionid | string | true | ID della regione che genera l’evento. |
| regioneventtype | int | true | Tipo di evento regione da generare. 1 per l'ingresso e 2 per l'uscita. |

## Eventi inviati dall'estensione Luoghi

Informazioni in corso.

