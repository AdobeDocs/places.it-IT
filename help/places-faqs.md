---
title: Domande frequenti
description: Questo argomento fornisce informazioni aggiuntive su alcune domande frequenti.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 1%

---

# Domande frequenti

Seguono alcune informazioni e domande frequenti su Places Service.

## Migrazione da trackLocation nel SDK v4

Se stai eseguendo la migrazione dal SDK v4 e stai cercando un sostituto dell&#39;API `trackLocation`, consulta l&#39;argomento [Utilizzare il servizio Places senza il monitoraggio dell&#39;area attiva](use-places-without-active-monitoring.md).

## Dimensioni e affidabilità

Importante da notare per tutti i recinti geografici utilizzati nel monitoraggio di aree geografiche da un’app mobile, indipendentemente dall’utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere presenti durante la creazione di recinti geografici. Per la massima affidabilità, i recinti geografici devono avere un raggio di almeno 100 metri. È possibile creare recinti geografici più piccoli, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l’utente ha smesso di spostarsi per un certo periodo.

Inoltre, l&#39;accuratezza e l&#39;affidabilità possono essere ridotte in base alle condizioni hardware, come il wi-fi spento o non disponibile, e anche in base alla posizione del dispositivo in relazione all&#39;intralcio ai segnali GPS. Ad esempio, le aree montane, le aree urbane e le aree interne possono ridurre la precisione di posizionamento dai sistemi operativi iOS e Android.

## Come si attiva un evento di uscita?

Il monitoraggio dell’area geografica implementato deve richiedere un elenco dei punti di interesse nelle vicinanze. Una volta ricevuta, un’area geografica deve essere registrata con il sistema operativo per ogni POI. Il sistema operativo è ora responsabile della notifica al SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. SDK attiva un evento di uscita solo quando il sistema operativo notifica al SDK che l&#39;evento si è verificato. Il motivo principale di questa notifica è la riservatezza temporale dei dati relativi alla posizione.

Se il sistema operativo non è in grado di fornire un evento di uscita quando il dispositivo lascia un’area geografica, è più sicuro che SDK si limiti a omettere l’evento di uscita. Se SDK produce un evento di uscita senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento di uscita venga elaborato ben oltre il periodo di tempo durante il quale il dispositivo era vicino al POI.

## Numero di POI

Nell’interfaccia di gestione dei punti di interesse di Places Service, i clienti possono aggiungere fino a 150 mila punti di interesse in una libreria specifica. Se necessario, i clienti possono definire più librerie per segmentare i raggruppamenti di POI.

## Alcune note sulla modifica della posizione e sul monitoraggio dell’area attiva

Il monitoraggio di una regione geografica inizia immediatamente dopo la registrazione per le app autorizzate. Tuttavia, non aspettarti di ricevere un evento immediatamente, perché solo gli attraversamenti dei confini generano un evento. In particolare, se la posizione dell’utente si trova già all’interno dell’area al momento della registrazione, il gestore della posizione non genera automaticamente un evento. L’app deve invece attendere che l’utente superi il limite dell’area geografica prima che venga generato un evento e inviato al delegato.

Quando si specifica l&#39;insieme di regioni da monitorare, è necessario essere prudenti. Le aree sono una risorsa di sistema condivisa e il numero totale di aree disponibili a livello di sistema è limitato. Per questo motivo, la Posizione core limita a 20 il numero di aree che possono essere monitorate simultaneamente da una singola app. Per aggirare questo limite, è consigliabile registrare solo le aree nelle immediate vicinanze dell’utente.

[Ulteriori informazioni sul sito per sviluppatori Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
