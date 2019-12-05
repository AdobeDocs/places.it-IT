---
title: Domande frequenti
seo-title: Domande frequenti
description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
seo-description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
translation-type: tm+mt
source-git-commit: f4b8bccc154df346e67ef17295d7c6b42c68b26d

---


# Domande frequenti

Seguono alcune informazioni e domande frequenti su Location Service.

## Dimensioni e affidabilità

Importante da notare che tutte le aree geografiche utilizzate nel monitoraggio regionale da un'app mobile indipendentemente dall'utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere a mente durante la creazione di aree geografiche. Per la massima affidabilità, le aree geografiche devono avere un raggio di almeno 100 metri. È possibile creare aree geografiche più piccole, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l'utente ha smesso di muoversi per un periodo.

Inoltre, la precisione e l'affidabilità possono essere ridotte in base a condizioni hardware come lo spegnimento o la mancata disponibilità del wi-fi, e anche in base alla posizione del dispositivo in relazione all'impedimento dei segnali GPS. Ad esempio, le aree montane, le impostazioni urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## In che modo viene attivato un evento exit?

Quando l’SDK (Places Monitor) riceve un nuovo elenco di POI vicini, registra una regione con il sistema operativo per ciascun POI. Il sistema operativo ora è responsabile della notifica dell’SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L'SDK attiva un evento exit solo quando il sistema operativo notifica all'SDK che l'evento si è verificato. Il motivo principale di questa notifica è la sensibilità temporale dei dati sulla posizione.

Se il sistema operativo non è in grado di fornire un evento exit quando il dispositivo lascia un'area, è più sicuro che l'SDK ometta semplicemente l'evento exit. Se l’SDK produce un evento exit senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento exit venga elaborato correttamente al di fuori del periodo di tempo durante il quale il dispositivo si trovava vicino al POI.
