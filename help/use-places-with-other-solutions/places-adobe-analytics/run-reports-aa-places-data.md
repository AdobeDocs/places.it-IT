---
title: Aggiungere contesto di posizione alle richieste di Analytics
description: Questa sezione fornisce informazioni su come aggiungere contesto di posizione alle richieste di Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 1%

---

# Aggiungere contesto di posizione alle richieste di Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In questo documento si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull’implementazione di Places Service, consulta [Estensioni Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo l’invio degli eventi di entrata e uscita da Places Service, puoi creare regole nel Experience Platform Launch e allegare i dati di Places Service a tutti gli eventi di Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## 1. Creare una regola

1. Il giorno **[!UICONTROL Regole]** , fare clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:
   * Se non disponi di regole esistenti per questa proprietà, **[!UICONTROL Crea nuova regola]** al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Crea nuova regola]** in alto a destra.

## 2.Selezionare un evento

1. Assegna alla regola un nome significativo in modo che sia facilmente riconoscibile nell’elenco delle regole.

   In questo esempio, la regola è denominata **[!UICONTROL Allega dati del servizio Places agli eventi di tracciamento delle azioni di Analytics]**.

1. Sotto **[!UICONTROL Eventi]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Core mobile]**.

1. Dalla sezione **[!UICONTROL Tipo di evento]** elenco a discesa, seleziona **[!UICONTROL Azione di tracciamento]**.

Ora puoi determinare i trigger da includere per questa regola. In questo esempio, il trigger si basa su tutti `TrackAction` chiamate. Dopo aver configurato l’evento, fai clic su **[!UICONTROL Mantieni modifiche]**.

![&quot;crea un evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Aggiungere condizioni

>[!IMPORTANT]
>
>Completa questa procedura per aggiungere Condizioni alla regola. In caso contrario, vai al *Definire l’azione* sezione successiva.

In questo esempio, viene creata una condizione per cui la regola viene attivata solo per i clienti AT&amp;T.

1. Sotto **[!UICONTROL Condizioni]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Core mobile]**.

1. Dalla sezione **[!UICONTROL Tipo di condizione]** elenco a discesa, seleziona **[!UICONTROL Nome gestore]**.

1. Nella finestra a destra, seleziona la **[!UICONTROL AT&amp;T]** casella di controllo.

1. Clic **[!UICONTROL Mantieni modifiche]**.

![&quot;crea una condizione&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definire l’azione

1. Sotto **[!UICONTROL Azioni]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Core mobile]**.

1. Dalla sezione **[!UICONTROL Tipo di azione]** elenco a discesa, seleziona **[!UICONTROL Allega dati]**.

1. Nel riquadro di destra, nella **[!UICONTROL Payload JSON]** digitare i dati che verranno aggiunti a questo evento.

1. Clic **[!UICONTROL Mantieni modifiche]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che un’estensione che è in ascolto di questo evento possa sentire l’evento. In questo esempio, alcuni dati contestuali vengono aggiunti a questo evento prima che l’estensione Analytics lo elabori. I dati contestuali aggiunti ora si trovano nell’hit di Analytics in uscita.

Nell&#39;esempio seguente, `poi.city` e `poi.name` I valori vengono aggiunti ai dati contestuali dell’evento Analytics. I valori per le nuove chiavi vengono determinati dinamicamente dall&#39;SDK quando questo evento viene elaborato.

![&quot;crea un’azione&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;la regola è completa.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
