---
title: Inviare dati di entrata e uscita POI ad Analytics
description: Questa sezione fornisce informazioni su come inviare dati di ingresso e uscita POI ad Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# Inviare dati di entrata e uscita POI ad Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>In questa sezione si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni di Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo l’invio degli eventi di entrata e uscita da Places Service, puoi creare regole di Experience Platform Launch per inviare i dati di Places Service ad Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## 1. Creare una regola

1. Nella scheda **[!UICONTROL Regole]**, fai clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:

   * Se non disponi di regole esistenti per questa proprietà, il pulsante **[!UICONTROL Crea nuova regola]** sarà al centro della schermata.
   * Se la proprietà dispone di regole, il pulsante **[!UICONTROL Crea nuova regola]** si trova in alto a destra nella schermata.

## 2. Seleziona un evento

1. Digita un nome significativo per la regola.

   In questo modo, la regola sarà facilmente riconoscibile nell’elenco delle regole. In questo esempio, la regola è denominata **[!UICONTROL Send Data to Analytics]**.

1. Nella sezione **[!UICONTROL Events]**, fai clic su **[!UICONTROL Add]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Places Service]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo evento]**, selezionare **[!UICONTROL Inserisci POI]**.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

   ![&quot;seleziona un evento&quot;](/help/assets/pt-selectEvent.png)


## 3. Aggiungere condizioni

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


## 4. Definire l’azione

1. Nella sezione **[!UICONTROL Azioni]**, fai clic su **[!UICONTROL Aggiungi]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Adobe Analytics]**.

1. Dall&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Traccia]**.

1. Nel riquadro a destra, aggiungi l’azione o lo stato che desideri inviare ad Analytics.

   Puoi anche scegliere di aggiungere dati contestuali aggiuntivi a questa richiesta. Ricorda che puoi utilizzare gli elementi dati per ottenere questi dati in modo dinamico dall’SDK.

1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

   Nell&#39;esempio seguente, viene inviata una chiamata `TrackAction` ad Analytics con dati di contesto aggiuntivi di `poi.name` uguali al nome del punto di interesse che ha attivato questo evento di ingresso:

   ![&quot;ha impostato un&#39;azione&quot;](/help/assets/pt-setAction.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;regola creata&quot;](/help/assets/pt-ruleComplete.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
