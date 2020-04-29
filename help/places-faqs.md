---
title: Domande frequenti
description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9

---


# Domande frequenti

Seguono alcune informazioni e domande frequenti su Places Service.

## Migrazione da trackLocation nell’SDK v4

Se state eseguendo la migrazione dall’SDK v4 e state cercando di sostituire l’ `trackLocation` API, fate riferimento all’argomento [Usa servizio Luoghi senza monitoraggio](use-places-without-active-monitoring.md)area attiva.

## Dimensioni e affidabilità

Importante da notare che tutte le aree geografiche utilizzate nel monitoraggio regionale da un&#39;app mobile indipendentemente dall&#39;utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere a mente durante la creazione di aree geografiche. Per la massima affidabilità, le aree geografiche devono avere un raggio di almeno 100 metri. È possibile creare aree geografiche più piccole, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l&#39;utente ha smesso di muoversi per un periodo.

Inoltre, la precisione e l&#39;affidabilità possono essere ridotte in base a condizioni hardware come lo spegnimento o la mancata disponibilità del wi-fi, e anche in base alla posizione del dispositivo in relazione all&#39;impedimento dei segnali GPS. Ad esempio, le aree montane, le impostazioni urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## In che modo viene attivato un evento exit?

Quando l’SDK (Places Monitor) riceve un nuovo elenco di POI vicini, registra una regione con il sistema operativo per ciascun POI. Il sistema operativo ora è responsabile della notifica dell’SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L&#39;SDK attiva un evento exit solo quando il sistema operativo notifica all&#39;SDK che l&#39;evento si è verificato. Il motivo principale di questa notifica è la sensibilità temporale dei dati sulla posizione.

Se il sistema operativo non è in grado di fornire un evento exit quando il dispositivo lascia un&#39;area, è più sicuro che l&#39;SDK ometta semplicemente l&#39;evento exit. Se l’SDK produce un evento exit senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento exit possa essere elaborato correttamente al di fuori del periodo di tempo durante il quale il dispositivo si trovava vicino al POI.

## Numero di POI

Nell&#39;interfaccia di gestione di Places Service POI, i clienti possono aggiungere fino a 150 mila punti di interesse in una libreria specifica. Se necessario, i clienti possono definire più librerie per segmentare i raggruppamenti di POI.

## Alcune note sulla modifica della posizione e sul monitoraggio attivo della regione

Il monitoraggio di un&#39;area geografica inizia subito dopo la registrazione per le app autorizzate. Tuttavia, non aspettatevi di ricevere immediatamente un evento, perché solo i passaggi dei bordi generano un evento. In particolare, se la posizione dell&#39;utente è già all&#39;interno della regione al momento della registrazione, il manager della posizione non genera automaticamente un evento. Al contrario, l&#39;app deve aspettare che l&#39;utente oltrepassi il limite della regione prima che un evento venga generato e inviato al delegato.

Sii prudente quando specifica il set di regioni da monitorare. Le regioni sono una risorsa di sistema condivisa e il numero totale di regioni disponibili a livello di sistema è limitato. Per questo motivo, la Posizione di base limita a 20 il numero di aree che possono essere monitorate simultaneamente da una singola app. Per aggirare questo limite, è consigliabile registrare solo le aree nelle immediate vicinanze dell’utente.

[Consultate ulteriori informazioni sul sito] per sviluppatori Apple (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
