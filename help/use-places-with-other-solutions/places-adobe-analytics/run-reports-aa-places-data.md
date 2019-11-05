---
title: Eseguire rapporti in Adobe Analytics che includono i dati Luoghi
seo-title: Eseguire rapporti in Adobe Analytics che includono i dati Luoghi
description: Questa sezione fornisce informazioni su come eseguire i report in Analytics che includono i dati Luoghi.
seo-description: Questa sezione fornisce informazioni su come eseguire i report in Analytics che includono i dati Luoghi.
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Eseguire rapporti in Adobe Analytics che includono i dati Luoghi {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Questo documento presuppone che nell'applicazione sia implementato Adobe Places. Per ulteriori informazioni sull'implementazione di Adobe Places, consultate Estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

Dopo che Places invia gli eventi di entrata e uscita, puoi creare regole in Experience Platform Launch e allegare i dati di Places a tutti gli eventi di Adobe Analytics. Per creare questo tipo di regola, selezionate la proprietà in Lancio e completate i seguenti passaggi:

## 1. Creare una regola

1. Nella **[!UICONTROL Rules]** scheda fare clic su **[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:
   * Se non sono presenti regole per questa proprietà, il **[!UICONTROL Create New Rule]** pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Create New Rule]** pulsante si trova in alto a destra nella schermata.

## 2.Selezionare un evento

1. Attribuite alla regola un nome significativo in modo che possa essere facilmente riconoscibile nell'elenco delle regole.

   In questo esempio, la regola viene denominata **[!UICONTROL Attach Places Data to Analytics Track Action Events]**.

1. Nella **[!UICONTROL Events]** sezione fare clic su **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Event Type]** discesa, selezionate **[!UICONTROL Track Action]**.

Ora puoi determinare quali attivatori includere per questa regola. In questo esempio, il trigger è basato su tutte le `TrackAction` chiamate. Dopo aver configurato l’evento, fate clic su **[!UICONTROL Keep Changes]**.

!["create a event"](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completate questa procedura per aggiungere le condizioni alla regola. In caso contrario, passare alla sezione *Definisci azione* seguente.

In questo esempio, viene creata una condizione che determina l'attivazione della regola solo per i clienti AT&amp;T.

1. Nella **[!UICONTROL Conditions]** sezione fare clic su **[!UICONTROL Add]**.

1. Dall'elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTORL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Condition Type]** discesa, selezionate **[!UICONTROL Carrier Name]**.

1. Nella finestra a destra, selezionate la **[!UICONTROL AT&T]** casella di controllo.

1. Fai clic su **[!UICONTROL Keep Changes]**.

!["create una condizione"](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definire l'azione

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Action Type]** discesa, selezionate **[!UICONTROL Attach Data]**.

1. Nel riquadro di destra, nel **[!UICONTROL JSON Payload]** campo, digitare i dati che verranno aggiunti a questo evento.

1. Fai clic su **[!UICONTROL Keep Changes]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che un'estensione in ascolto di questo evento possa sentire l'evento. In questo esempio, alcuni dati contestuali vengono aggiunti a questo evento prima che l'estensione Analytics lo elabori. I dati contestuali aggiunti ora si trovano nell'hit Analytics in uscita.

Nell'esempio seguente, `poi.city` e `poi.name` i valori vengono aggiunti ai dati contestuali dell'evento Analytics. I valori delle nuove chiavi sono determinati dinamicamente dall'SDK quando questo evento viene elaborato.

!["create un'azione"](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l'aspetto seguente:

!["la regola è completa."](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Fai clic su **[!UICONTROL Save]**

1. Generate di nuovo la proprietà Launch e distribuitela nell'ambiente corretto.
