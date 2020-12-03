---
title: Inviare dati di entrata e uscita POI ad Analytics
description: Questa sezione fornisce informazioni su come inviare i dati di entrata e uscita dal POI ad Analytics.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---


# Inviare dati di entrata e uscita POI ad Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Questa sezione presuppone che nell&#39;applicazione sia implementato il servizio Luoghi. Per ulteriori informazioni sull&#39;implementazione di Places Service, vedere [Estensioni](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

Dopo che il servizio Luoghi invia gli eventi di entrata e uscita, puoi creare le regole nel Experience Platform Launch per inviare i dati del servizio Luoghi a  Adobe Analytics. Per creare questo tipo di regola, selezionate la proprietà in Lancio e completate i seguenti passaggi:

## 1. Creare una regola

1. Nella scheda **[!UICONTROL Rules]** fai clic su **[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:

   * Se non sono presenti regole per questa proprietà, il **[!UICONTROL Create New Rule]** pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Create New Rule]** pulsante si trova in alto a destra nella schermata.

## 2. Selezione di un evento

1. Digitate un nome significativo per la regola.

   In questo modo, la regola sarà facilmente riconoscibile nell&#39;elenco delle regole. In questo esempio, la regola viene denominata **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Places Service]**.

1. Dall’elenco a **[!UICONTROL Event Type]** discesa, selezionate **[!UICONTROL Enter POI]**.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   ![&quot;select a event&quot;](/help/assets/pt-selectEvent.png)


## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio per aggiungere condizioni alla regola. In caso contrario, passare a *Definisci azione* .

In questo esempio, viene creata una condizione che determina l’attivazione della regola solo quando il nome del POI corrente è uguale a **[!UICONTROL My POI]**.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Places Service]**.

1. Dall’elenco a **[!UICONTROL Condition Type]** discesa, selezionate **[!UICONTROL Name]**.

1. Nel riquadro a destra, nel campo di testo, immettere **[!UICONTROL My POI]**.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   ![&quot;imposta una condizione&quot;](/help/assets/pt-setCondition.png)


## 4. Definire l&#39;azione

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Adobe Analytics]**.

1. Dall’elenco a **[!UICONTROL Action Type]** discesa, selezionate **[!UICONTROL Track]**.

1. Nel riquadro a destra, aggiungi l’azione o lo stato da inviare ad Analytics.

   Potete anche scegliere di aggiungere eventuali dati contestuali aggiuntivi a questa richiesta. Ricorda che puoi utilizzare gli elementi dati per ottenere questi dati in modo dinamico dall’SDK.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   Nell’esempio seguente, una `TrackAction` chiamata viene inviata ad Analytics con dati di contesto aggiuntivi `poi.name` uguali al nome del POI che ha attivato questo evento di voce:

   ![&quot;imposta un&#39;azione&quot;](/help/assets/pt-setAction.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l&#39;aspetto seguente:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Fai clic su **[!UICONTROL Save]**.

1. Generate di nuovo la proprietà Launch e distribuitela nell&#39;ambiente corretto.
