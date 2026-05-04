---
title: Aggiungere contesto di posizione alle richieste di Analytics
description: Questa sezione fornisce informazioni su come aggiungere contesto di posizione alle richieste di Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
TQID: https://experienceleague.adobe.com/NR-CowJgzUBMVWcbV-EvdyBDsiwLi72yxM-Vjx5oNwk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 2%

---

# Aggiungere contesto di posizione alle richieste di Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In questo documento si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni di Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo l’invio degli eventi di entrata e uscita da Places Service, puoi creare regole in Experience Platform Launch e allegare i dati di Places Service a tutti gli eventi di Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## &#x200B;1. Creare una regola

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


## &#x200B;3. Aggiungi condizioni

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

## &#x200B;4. Definire l’azione

1. Nella sezione **[!UICONTROL Azioni]**, fai clic su **[!UICONTROL Aggiungi]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Allega dati]**.

1. Nel riquadro di destra, nel campo **[!UICONTROL Payload JSON]**, digitare i dati che verranno aggiunti a questo evento.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che un’estensione in ascolto di questo evento possa ascoltare l’evento. In questo esempio, alcuni dati contestuali vengono aggiunti a questo evento prima che l’estensione Analytics lo elabori. I dati contestuali aggiunti ora si trovano nell’hit di Analytics in uscita.

Nell&#39;esempio seguente, i valori `poi.city` e `poi.name` vengono aggiunti ai dati contestuali dell&#39;evento Analytics. I valori per le nuove chiavi vengono determinati dinamicamente da SDK quando questo evento viene elaborato.

![&quot;crea un&#39;azione&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## &#x200B;5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;regola completata.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
