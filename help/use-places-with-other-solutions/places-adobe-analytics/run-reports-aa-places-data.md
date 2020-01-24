---
title: Aggiunta di un contesto di posizione alle richieste di Analytics
description: Questa sezione fornisce informazioni su come aggiungere il contesto della posizione alle richieste di Analytics.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Aggiunta di un contesto di posizione alle richieste di Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Questo documento presuppone che nell&#39;applicazione sia implementato il servizio Luoghi. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

Dopo che il servizio Luoghi invia gli eventi di entrata e uscita, puoi creare regole in Experience Platform Launch e allegare i dati del servizio Luoghi a tutti gli eventi di Adobe Analytics. Per creare questo tipo di regola, selezionate la proprietà in Lancio e completate i seguenti passaggi:

## 1. Creare una regola

1. Nella **[!UICONTROL Rules]**scheda fare clic su**[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:
   * Se non sono presenti regole per questa proprietà, il **[!UICONTROL Create New Rule]**pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Create New Rule]**pulsante si trova in alto a destra nella schermata.

## 2.Selezionare un evento

1. Attribuite alla regola un nome significativo in modo che possa essere facilmente riconoscibile nell&#39;elenco delle regole.

   In questo esempio, la regola viene denominata **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Nella **[!UICONTROL Events]**sezione fare clic su**[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]**discesa, selezionate**[!UICONTROL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Event Type]**discesa, selezionate**[!UICONTROL Track Action]**.

Ora puoi determinare quali attivatori includere per questa regola. In questo esempio, il trigger è basato su tutte le `TrackAction` chiamate. Dopo aver configurato l’evento, fate clic su **[!UICONTROL Keep Changes]**.

![&quot;create a event&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completate questa procedura per aggiungere le condizioni alla regola. In caso contrario, passare alla sezione *Definisci azione* seguente.

In questo esempio, viene creata una condizione che determina l&#39;attivazione della regola solo per i clienti AT&amp;T.

1. Nella **[!UICONTROL Conditions]**sezione fare clic su**[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]**discesa, selezionate**[!UICONTROL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Condition Type]**discesa, selezionate**[!UICONTROL Carrier Name]**.

1. Nella finestra a destra, selezionate la **[!UICONTROL AT&T]**casella di controllo.

1. Fai clic su **[!UICONTROL Keep Changes]**.

![&quot;create una condizione&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definire l&#39;azione

1. Nella **[!UICONTROL Actions]**sezione fare clic su**[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]**discesa, selezionate**[!UICONTROL Mobile Core]**.

1. Dall’elenco a **[!UICONTROL Action Type]**discesa, selezionate**[!UICONTROL Attach Data]**.

1. Nel riquadro di destra, nel **[!UICONTROL JSON Payload]**campo, digitare i dati che verranno aggiunti a questo evento.

1. Fai clic su **[!UICONTROL Keep Changes]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che un&#39;estensione in ascolto di questo evento possa sentire l&#39;evento. In questo esempio, alcuni dati contestuali vengono aggiunti a questo evento prima che l&#39;estensione Analytics lo elabori. I dati contestuali aggiunti ora si trovano nell&#39;hit Analytics in uscita.

Nell&#39;esempio seguente, `poi.city` e `poi.name` i valori vengono aggiunti ai dati contestuali dell&#39;evento Analytics. I valori delle nuove chiavi sono determinati dinamicamente dall&#39;SDK quando questo evento viene elaborato.

![&quot;create un&#39;azione&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l&#39;aspetto seguente:

![&quot;la regola è completa.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Fai clic su **[!UICONTROL Save]**

1. Generate di nuovo la proprietà Launch e distribuitela nell&#39;ambiente corretto.
