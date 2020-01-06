---
title: Domande frequenti
description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Domande frequenti

Seguono alcune informazioni e domande frequenti su Location Service.

## Dimensioni e affidabilità

Importante da notare che tutte le aree geografiche utilizzate nel monitoraggio regionale da un&#39;app mobile indipendentemente dall&#39;utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere a mente durante la creazione di aree geografiche. Per la massima affidabilità, le aree geografiche devono avere un raggio di almeno 100 metri. È possibile creare aree geografiche più piccole, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l&#39;utente ha smesso di muoversi per un periodo.

Inoltre, la precisione e l&#39;affidabilità possono essere ridotte in base a condizioni hardware come lo spegnimento o la mancata disponibilità del wi-fi, e anche in base alla posizione del dispositivo in relazione all&#39;impedimento dei segnali GPS. Ad esempio, le aree montane, le impostazioni urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## In che modo viene attivato un evento exit?

Quando l’SDK (Places Monitor) riceve un nuovo elenco di POI vicini, registra una regione con il sistema operativo per ciascun POI. Il sistema operativo ora è responsabile della notifica dell’SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L&#39;SDK attiva un evento exit solo quando il sistema operativo notifica all&#39;SDK che l&#39;evento si è verificato. Il motivo principale di questa notifica è la sensibilità temporale dei dati sulla posizione.

Se il sistema operativo non è in grado di fornire un evento exit quando il dispositivo lascia un&#39;area, è più sicuro che l&#39;SDK ometta semplicemente l&#39;evento exit. Se l’SDK produce un evento exit senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento exit venga elaborato correttamente al di fuori del periodo di tempo durante il quale il dispositivo si trovava vicino al POI.
