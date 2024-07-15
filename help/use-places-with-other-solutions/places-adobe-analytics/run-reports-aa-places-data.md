---
title: Aggiungere contesto di posizione alle richieste di Analytics
description: Questa sezione fornisce informazioni su come aggiungere contesto di posizione alle richieste di Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# Aggiungere contesto di posizione alle richieste di Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In questo documento si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni di Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo l’invio degli eventi di entrata e uscita da Places Service, puoi creare regole nel Experience Platform Launch e allegare i dati di Places Service a tutti gli eventi di Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## 1. Creare una regola

1. Nella scheda **[!UICONTROL Regole]**, fai clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:
   * Se non disponi di regole esistenti per questa proprietà, il pulsante **[!UICONTROL Crea nuova regola]** sarà al centro della schermata.
   * Se la proprietà dispone di regole, il pulsante **[!UICONTROL Crea nuova regola]** si trova in alto a destra nella schermata.

## 2.Selezionare un evento

1. Assegna alla regola un nome significativo in modo che sia facilmente riconoscibile nell’elenco delle regole.

   In questo esempio, la regola è denominata **[!UICONTROL Allega dati del servizio Places agli eventi di tracciamento delle azioni di Analytics]**.

1. Nella sezione **[!UICONTROL Events]**, fai clic su **[!UICONTROL Add]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo evento]**, selezionare **[!UICONTROL Azione traccia]**.

Ora puoi determinare i trigger da includere per questa regola. In questo esempio, il trigger si basa su tutte le chiamate `TrackAction`. Dopo aver configurato l&#39;evento, fare clic su **[!UICONTROL Mantieni modifiche]**.

![&quot;crea un evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Aggiungere condizioni

>[!IMPORTANT]
>
>Completa questa procedura per aggiungere Condizioni alla regola. In caso contrario, passa alla sezione *Definisci l&#39;azione* di seguito.

In questo esempio, viene creata una condizione per cui la regola viene attivata solo per i clienti AT&amp;T.

1. Nella sezione **[!UICONTROL Conditions]**, fai clic su **[!UICONTROL Add]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo condizione]**, selezionare **[!UICONTROL Nome gestore]**.

1. Nella finestra a destra, seleziona la casella di controllo **[!UICONTROL AT&amp;T]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

![&quot;crea una condizione&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definire l’azione

1. Nella sezione **[!UICONTROL Azioni]**, fai clic su **[!UICONTROL Aggiungi]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Allega dati]**.

1. Nel riquadro di destra, nel campo **[!UICONTROL Payload JSON]**, digitare i dati che verranno aggiunti a questo evento.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che un’estensione che è in ascolto di questo evento possa sentire l’evento. In questo esempio, alcuni dati contestuali vengono aggiunti a questo evento prima che l’estensione Analytics lo elabori. I dati contestuali aggiunti ora si trovano nell’hit di Analytics in uscita.

Nell&#39;esempio seguente, i valori `poi.city` e `poi.name` vengono aggiunti ai dati contestuali dell&#39;evento Analytics. I valori per le nuove chiavi vengono determinati dinamicamente dall&#39;SDK quando questo evento viene elaborato.

![&quot;crea un&#39;azione&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;regola completata.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
