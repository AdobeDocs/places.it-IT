---
title: Inviare dati di entrata e uscita POI ad Analytics
description: Questa sezione fornisce informazioni su come inviare dati di ingresso e uscita POI ad Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 1%

---

# Inviare dati di entrata e uscita POI ad Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>In questa sezione si presuppone che nell’applicazione sia stato implementato Places Service. Per ulteriori informazioni sull’implementazione di Places Service, consulta [Estensioni Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo l’invio degli eventi di entrata e uscita da Places Service, puoi creare regole di Experience Platform Launch per inviare i dati di Places Service ad Adobe Analytics. Per creare questo tipo di regola, seleziona la proprietà in Launch e completa i passaggi seguenti:

## 1. Creare una regola

1. Il giorno **[!UICONTROL Regole]** , fare clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:

   * Se non disponi di regole esistenti per questa proprietà, **[!UICONTROL Crea nuova regola]** al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Crea nuova regola]** in alto a destra.

## 2. Seleziona un evento

1. Digita un nome significativo per la regola.

   In questo modo, la regola sarà facilmente riconoscibile nell’elenco delle regole. In questo esempio, la regola è denominata **[!UICONTROL Inviare dati ad Analytics]**.

1. In **[!UICONTROL Eventi]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places Service]**.

1. Dalla sezione **[!UICONTROL Tipo di evento]** elenco a discesa, seleziona **[!UICONTROL Inserisci POI]**.

1. Clic **[!UICONTROL Mantieni modifiche]**.

   ![&quot;seleziona un evento&quot;](/help/assets/pt-selectEvent.png)


## 3. Aggiungere condizioni

>[!IMPORTANT]
>
>Completa questo passaggio per aggiungere Condizioni alla regola. In caso contrario, vai a *Definire l’azione* di seguito.

In questo esempio, viene creata una condizione per cui la regola viene attivata solo quando il nome del punto di interesse corrente è uguale a **[!UICONTROL I miei POI]**.

1. Sotto **[!UICONTROL Condizioni]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Places Service]**.

1. Dalla sezione **[!UICONTROL Tipo di condizione]** elenco a discesa, seleziona **[!UICONTROL Nome]**.

1. Nel riquadro di destra, nel campo di testo, immettere **[!UICONTROL I miei POI]**.

1. Clic **[!UICONTROL Mantieni modifiche]**.

   ![&quot;imposta una condizione&quot;](/help/assets/pt-setCondition.png)


## 4. Definire l’azione

1. Sotto **[!UICONTROL Azioni]** , fare clic su **[!UICONTROL Aggiungi]**.

1. Dalla sezione **[!UICONTROL Estensione]** elenco a discesa, seleziona **[!UICONTROL Adobe Analytics]**.

1. Dalla sezione **[!UICONTROL Tipo di azione]** elenco a discesa, seleziona **[!UICONTROL Traccia]**.

1. Nel riquadro a destra, aggiungi l’azione o lo stato che desideri inviare ad Analytics.

   Puoi anche scegliere di aggiungere dati contestuali aggiuntivi a questa richiesta. Ricorda che puoi utilizzare gli elementi dati per ottenere questi dati in modo dinamico dall’SDK.

1. Clic **[!UICONTROL Mantieni modifiche]**.

   Nell’esempio seguente, un’ `TrackAction` La chiamata viene inviata ad Analytics con dati contestuali aggiuntivi di `poi.name` è uguale al nome del POI che ha attivato questo evento di ingresso:

   ![&quot;imposta un&#39;azione&quot;](/help/assets/pt-setAction.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![&quot;regola creata&quot;](/help/assets/pt-ruleComplete.png)

1. Fai clic su **[!UICONTROL Salva]**

1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
