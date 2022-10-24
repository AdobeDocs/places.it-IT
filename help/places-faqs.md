---
title: Domande frequenti
description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Domande frequenti

Seguono alcune informazioni e domande frequenti su Places Service.

## Migrazione da trackLocation nell’SDK v4

Se esegui la migrazione dall’SDK v4 e stai cercando una sostituzione con `trackLocation` API, fai riferimento all&#39;argomento [Utilizzare il servizio Places senza monitoraggio di aree attive](use-places-without-active-monitoring.md).

## Dimensioni e affidabilità

Importante da notare per tutti i recinti geografici utilizzati nel monitoraggio regionale da un’app mobile, indipendentemente dall’utilizzo di Adobe o di un altro servizio. I sistemi operativi consigliano alcuni parametri da tenere a mente durante la creazione di recinti geografici. Per garantire la massima affidabilità, i recinti geografici devono avere un raggio di almeno 100 metri. È possibile creare recinti geografici più piccoli, ma gli eventi di entrata e uscita potrebbero non essere generati o possono essere generati dopo che l’utente smette di muoversi per un periodo di tempo.

Inoltre, la precisione e l&#39;affidabilità possono essere ridotte in base a condizioni hardware come la disattivazione o l&#39;indisponibilità del wi-fi e anche in base alla posizione del dispositivo in relazione all&#39;impedimento dei segnali GPS. Ad esempio, le aree montane, le aree urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## Come si attiva un evento exit?

Il monitoraggio della regione implementato deve richiedere un elenco dei punti di interesse vicini. Una volta ricevuta, una regione deve essere registrata con il sistema operativo per ciascun POI. Il sistema operativo ora è responsabile della notifica dell&#39;SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L&#39;SDK attiva un evento di uscita solo quando il sistema operativo notifica all&#39;SDK che l&#39;evento si è verificato. Il motivo principale di questa notifica è la sensibilità temporale dei dati sulla posizione.

Se il sistema operativo non è in grado di fornire un evento di uscita quando il dispositivo lascia una regione, è più sicuro che l&#39;SDK ometta semplicemente l&#39;evento di uscita. Se l&#39;SDK produce un evento di uscita senza che l&#39;evento sia attivato dal sistema operativo, esiste il rischio che l&#39;evento di uscita venga elaborato ben al di fuori del periodo di tempo durante il quale il dispositivo si trovava vicino al POI.

## Numero di POI

Nell’interfaccia di gestione POI di Places Service, i clienti possono aggiungere fino a 150.000 punti di interesse in una libreria specifica. Se necessario, i clienti possono definire più librerie per segmentare i raggruppamenti di POI.

## Alcune note sulla modifica della posizione e sul monitoraggio attivo della regione

Il monitoraggio di una regione geografica inizia immediatamente dopo la registrazione per le app autorizzate. Tuttavia, non aspettarti di ricevere immediatamente un evento, perché solo i passaggi dei confini generano un evento. In particolare, se la posizione dell’utente è già all’interno della regione al momento della registrazione, il gestore della posizione non genera automaticamente un evento. Al contrario, l’app deve aspettare che l’utente attraversi il limite di regione prima che un evento venga generato e inviato al delegato.

Fai attenzione quando specifichi il set di regioni da monitorare. Le regioni sono una risorsa di sistema condivisa e il numero totale di regioni disponibili a livello di sistema è limitato. Per questo motivo, la posizione core limita a 20 il numero di aree che possono essere monitorate simultaneamente da una singola app. Per aggirare questo limite, è consigliabile registrare solo le aree nelle immediate vicinanze dell’utente.

[Vedi ulteriori informazioni sul sito per sviluppatori Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
