---
title: Domande frequenti
description: Questo argomento fornisce informazioni aggiuntive su alcune domande frequenti.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Domande frequenti

Seguono alcune informazioni e domande frequenti su Places Service.

## Migrazione da trackLocation nell’SDK v4

Se stai eseguendo la migrazione dall’SDK v4 e stai cercando un sostituto per `trackLocation` API, consulta l’argomento [Utilizza il servizio Places senza il monitoraggio dell’area attiva](use-places-without-active-monitoring.md).

## Dimensioni e affidabilità

Importante da notare per tutti i recinti geografici utilizzati nel monitoraggio di aree geografiche da un’app mobile, indipendentemente dall’utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere presenti durante la creazione di recinti geografici. Per la massima affidabilità, i recinti geografici devono avere un raggio di almeno 100 metri. È possibile creare recinti geografici più piccoli, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l’utente ha smesso di spostarsi per un certo periodo.

Inoltre, l&#39;accuratezza e l&#39;affidabilità possono essere ridotte in base alle condizioni hardware, come il wi-fi spento o non disponibile, e anche in base alla posizione del dispositivo in relazione all&#39;intralcio ai segnali GPS. Ad esempio, le aree montane, le aree urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## Come si attiva un evento di uscita?

Il monitoraggio dell’area geografica implementato deve richiedere un elenco dei punti di interesse nelle vicinanze. Una volta ricevuta, un’area geografica deve essere registrata con il sistema operativo per ogni POI. Il sistema operativo è ora responsabile della notifica all&#39;SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L&#39;SDK attiva un evento di uscita solo quando il sistema operativo notifica all&#39;SDK che l&#39;evento si è verificato. Il motivo principale di questa notifica è la riservatezza temporale dei dati relativi alla posizione.

Se il sistema operativo non è in grado di fornire un evento di uscita quando il dispositivo lascia un’area geografica, è più sicuro che l’SDK si limiti a omettere l’evento di uscita. Se l’SDK produce un evento di uscita senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento di uscita venga elaborato ben oltre il periodo di tempo durante il quale il dispositivo era vicino al POI.

## Numero di POI

Nell’interfaccia di gestione dei punti di interesse di Places Service, i clienti possono aggiungere fino a 150 mila punti di interesse in una libreria specifica. Se necessario, i clienti possono definire più librerie per segmentare i raggruppamenti di POI.

## Alcune note sulla modifica della posizione e sul monitoraggio dell’area attiva

Il monitoraggio di una regione geografica inizia immediatamente dopo la registrazione per le app autorizzate. Tuttavia, non aspettarti di ricevere un evento immediatamente, perché solo gli attraversamenti dei confini generano un evento. In particolare, se la posizione dell’utente si trova già all’interno dell’area al momento della registrazione, il gestore della posizione non genera automaticamente un evento. L’app deve invece attendere che l’utente superi il limite dell’area geografica prima che venga generato un evento e inviato al delegato.

Quando si specifica l&#39;insieme di regioni da monitorare, è necessario essere prudenti. Le aree sono una risorsa di sistema condivisa e il numero totale di aree disponibili a livello di sistema è limitato. Per questo motivo, la Posizione core limita a 20 il numero di aree che possono essere monitorate simultaneamente da una singola app. Per aggirare questo limite, è consigliabile registrare solo le aree nelle immediate vicinanze dell’utente.

[Consulta ulteriori informazioni sul sito per sviluppatori Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
