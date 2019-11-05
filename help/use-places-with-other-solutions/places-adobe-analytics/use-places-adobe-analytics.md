---
title: Invia dati Luoghi ad Adobe Analytics
seo-title: Invia dati Luoghi ad Adobe Analytics
description: Questa sezione fornisce informazioni su come inviare i dati Luoghi ad Analytics.
seo-description: Questa sezione fornisce informazioni su come inviare i dati Luoghi ad Analytics.
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Invia dati Luoghi ad Adobe Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Questa sezione presuppone che nell'applicazione siano implementate le posizioni. Per ulteriori informazioni sull'implementazione di Luoghi, vedere Estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

Dopo che Places invia gli eventi di entrata e uscita, puoi creare delle regole in Experience Platform Launch per inviare i dati Luoghi ad Adobe Analytics. Per creare questo tipo di regola, selezionate la proprietà in Lancio e completate i seguenti passaggi:

## 1. Creare una regola

1. Nella **[!UICONTROL Rules]** scheda fare clic su **[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:

   * Se non sono presenti regole per questa proprietà, il **[!UICONTROL Create New Rule]** pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il **[!UICONTROL Create New Rule]** pulsante si trova in alto a destra nella schermata.

## 2. Selezione di un evento

1. Digitate un nome significativo per la regola.

   In questo modo, la regola sarà facilmente riconoscibile nell'elenco delle regole. In questo esempio, la regola viene denominata **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Places]**.

1. Dall’elenco a **[!UICONTROL Event Type]** discesa, selezionate **[!UICONTROL Enter POI]**.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   !["select a event"](/help/assets/pt-selectEvent.png)


## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio per aggiungere condizioni alla regola. In caso contrario, passare a *Definisci azione* .

In questo esempio, viene creata una condizione che determina l’attivazione della regola solo quando il nome del POI corrente è uguale a **[!UICONTROL My POI]**.

1. Nella **[!UICONTROL Conditions]** sezione fare clic su **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Places]**.

1. Dall’elenco a **[!UICONTROL Condition Type]** discesa, selezionate **[!UICONTROL Name]**.

1. Nel riquadro a destra, nel campo di testo, immettere **[!UICONTROL My POI]**.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   !["imposta una condizione"](/help/assets/pt-setCondition.png)


## 4. Definire l'azione

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTROL Add]**.

1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Adobe Analytics]**.

1. Dall’elenco a **[!UICONTROL Action Type]** discesa, selezionate **[!UICONTROL Track]**.

1. Nel riquadro a destra, aggiungi l’azione o lo stato da inviare ad Analytics.

   Potete anche scegliere di aggiungere eventuali dati contestuali aggiuntivi a questa richiesta. Ricorda che puoi utilizzare gli elementi dati per ottenere questi dati in modo dinamico dall’SDK.

1. Fai clic su **[!UICONTROL Keep Changes]**.

   Nell’esempio seguente, una `TrackAction` chiamata viene inviata ad Analytics con dati di contesto aggiuntivi `poi.name` uguali al nome del POI che ha attivato questo evento di voce:

   !["imposta un'azione"](/help/assets/pt-setAction.png)

## 5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l'aspetto seguente:

!["rule is created"](/help/assets/pt-ruleComplete.png)

1. Fai clic su **[!UICONTROL Save]**

1. Generate di nuovo la proprietà Launch e distribuitela nell'ambiente corretto.
