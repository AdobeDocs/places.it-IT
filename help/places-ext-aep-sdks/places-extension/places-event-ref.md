---
title: Riferimento evento Luoghi
description: Elenco degli eventi gestiti dall’estensione Luoghi.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 13%

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
| raggio | intero | false | n/d | Raggio, in metri, utilizzato dalla ricerca di POI vicini. |
| conteggio | intero | false | 10 | Numero massimo di POI da restituire nell’evento di risposta risultante. |

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
