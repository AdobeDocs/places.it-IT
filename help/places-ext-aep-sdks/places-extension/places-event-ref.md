---
title: Riferimento evento Luoghi
description: Elenco degli eventi gestiti dall’estensione Luoghi.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 16%
---
# Riferimento evento Luoghi {#places-event-reference}

Elenco degli eventi gestiti dall’estensione Luoghi.

## GetCurrentPointsOfInterest

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descrizione evento**

Questo evento è una richiesta per recuperare i POI in cui si trova il dispositivo.

**Definizione payload dati**

n/d

## GetNearbyPointsOfInterest

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Descrizione evento**

Questo evento è una richiesta per ottenere i POI vicini tenendo in considerazione la posizione corrente del dispositivo e le librerie Places configurate.

**Definizione payload dati**

| Chiave | Tipo di valore | Obbligatorio | Valore predefinito | Descrizione |
| :--- | :--- | :--- | :--- | :--- |
| latitudine | doppio | true | n/d | Contiene il valore di latitudine per il centro della ricerca dei punti di interesse nelle vicinanze. |
| longitudine | doppio | true | n/d | Mantiene il valore di longitudine per il centro della ricerca dei punti di interesse nelle vicinanze. |
| raggio | intero | falso | n/d | Raggio, in metri, utilizzato dalla ricerca di POI vicini. |
| conteggio | intero | falso | 10 | Numero massimo di POI da restituire nell’evento di risposta risultante. |

## ProcessRegionEvent

**Dettagli evento**

| Tipo | Origine | Nome | Accoppiato |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Descrizione evento**

Questo evento fa sì che l’estensione Luoghi elabori un evento di entrata o uscita dal recinto geografico.

**Definizione payload dati**

| Chiave | Tipo di valore | Obbligatorio | Descrizione |
| :--- | :--- | :--- | :--- |
| regionid | stringa | true | ID della regione che genera l’evento. |
| regioneventtype | int | true | Tipo di evento dell’area geografica da generare. 1 per l&#39;ingresso e 2 per l&#39;uscita. |

## Eventi inviati dall’estensione Places

Queste informazioni sono attualmente in corso.
