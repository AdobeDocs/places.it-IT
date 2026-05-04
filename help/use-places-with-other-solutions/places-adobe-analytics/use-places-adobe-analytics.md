---
title: Inviare dati di entrata e uscita POI ad Analytics
description: Questa sezione fornisce informazioni su come inviare dati di ingresso e uscita POI ad Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
TQID: https://experienceleague.adobe.com/H-NkwK7KNSGPjEKYuWNc8F0f3MIu3wBr5FGjypxnqng
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
source-wordcount: 443
ht-degree: 3%

---

# Inviare dati di entrata e uscita POI ad Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>In questa sezione si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni di Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo che Places Service ha inviato gli eventi di entrata e uscita, puoi creare regole in Experience Platform Launch per inviare i dati di Places Service ad Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## &#x200B;1. Creare una regola

1. Nella scheda **[!UICONTROL Regole]**, fai clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:

   * Se non disponi di regole esistenti per questa proprietà, il pulsante **[!UICONTROL Crea nuova regola]** sarà al centro della schermata.
   * Se la proprietà dispone di regole, il pulsante **[!UICONTROL Crea nuova regola]** si trova in alto a destra nella schermata.

## &#x200B;2. Seleziona un evento

1. Digita un nome significativo per la regola.

   In questo modo, la regola sarà facilmente riconoscibile nell’elenco delle regole. In questo esempio, la regola è denominata **[!UICONTROL Send Data to Analytics]**.

1. Nella sezione **[!UICONTROL Events]**, fai clic su **[!UICONTROL Add]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Places Service]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo evento]**, selezionare **[!UICONTROL Inserisci POI]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

   ![&quot;seleziona un evento&quot;](/help/assets/pt-selectEvent.png)


## &#x200B;3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio per aggiungere Condizioni alla regola. In caso contrario, passa a *Definisci l&#39;azione* di seguito.

In questo esempio, viene creata una condizione che causa l&#39;attivazione della regola solo quando il nome del punto di interesse corrente è uguale a **[!UICONTROL Mio punto di interesse]**.

1. Nella sezione **[!UICONTROL Conditions]**, fai clic su **[!UICONTROL Add]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Places Service]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo di condizione]**, selezionare **[!UICONTROL Nome]**.

1. Nel campo di testo del riquadro di destra, immetti **[!UICONTROL My POI]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

   ![&quot;imposta una condizione&quot;](/help/assets/pt-setCondition.png)


## &#x200B;4. Definire l’azione

1. Nella sezione **[!UICONTROL Azioni]**, fai clic su **[!UICONTROL Aggiungi]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Adobe Analytics]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Traccia]**.

1. Nel riquadro a destra, aggiungi l’azione o lo stato che desideri inviare ad Analytics.

   Puoi anche scegliere di aggiungere dati contestuali aggiuntivi a questa richiesta. Ricorda che puoi utilizzare elementi dati per ottenere questi dati in modo dinamico da SDK.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

   Nell&#39;esempio seguente, viene inviata una chiamata `TrackAction` ad Analytics con dati di contesto aggiuntivi di `poi.name` uguali al nome del punto di interesse che ha attivato questo evento di ingresso:

   ![&quot;ha impostato un&#39;azione&quot;](/help/assets/pt-setAction.png)

## &#x200B;5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;regola creata&quot;](/help/assets/pt-ruleComplete.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
