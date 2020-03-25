---
title: Adobe Target
description: Questa sezione fornisce informazioni sull'utilizzo di Places Service con Adobe Target.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789

---


# Utilizzo del servizio Luoghi con Adobe Target {#places-target}

In questo documento si presuppone che l&#39;estensione Luoghi sia stata implementata nell&#39;applicazione. Per assistenza nell&#39;implementazione dell&#39;estensione Luoghi, vedere Estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

Dopo che l&#39;estensione Luoghi ha inviato eventi per voci ed uscite, puoi utilizzare Regole in Launch per allegare i dati del Servizio Luoghi agli eventi SDK di Adobe Target. Con la proprietà desiderata selezionata in Lancio, potete creare questo tipo di regola completando le seguenti attività:

## 1. Creare una regola

1. Nella scheda **[!UICONTROL Rules]** fai clic su **[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:

   * Se non sono presenti regole per questa proprietà, il pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il pulsante si trova in alto a destra nella schermata.

## 2. Selezionare un evento

1. Attribuite alla regola un nome significativo in modo che possa essere facilmente riconoscibile nell&#39;elenco delle regole.

   In questo esempio, la regola viene denominata **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Nella **[!UICONTROL Events]** sezione fare clic su **[!UICONTROL Add]**.
1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Adobe Target]**.
1. Dall’elenco a **[!UICONTROL Event Type]** discesa, selezionate **[!UICONTROL Content Requested]**.
1. Fai clic su **[!UICONTROL Keep Changes]**.

![aggiungere un evento](/help/assets/ad-setEvent_target.png)

## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio se desideri aggiungere Condizioni alla regola. In caso contrario, passare a *Definisci azione* .

Nell&#39;esempio seguente, viene creata una condizione che determina l&#39;attivazione della regola solo per gli utenti che hanno avviato l&#39;app cinque o più volte.

1. Nella **[!UICONTROL Conditions]** sezione fare clic su **[!UICONTROL Add]**.
1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.
1. Dall’elenco a **[!UICONTROL Condition Type]** discesa, selezionate **[!UICONTROL Launches]**.
1. Nel riquadro di destra, modificare l&#39;elenco a discesa e i controlli numerici in modo che la condizione sia letta **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Fai clic su **[!UICONTROL Keep Changes]**.

![aggiungere una condizione](/help/assets/ad-setCondition_target.png)

## 4. Definire l&#39;azione

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTROL Add]**.
1. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.
1. Dall’elenco a **[!UICONTROL Action Type]** discesa, selezionate **[!UICONTROL Attach Data]**.
1. Nel riquadro di destra, nel **[!UICONTROL JSON Payload]** campo, digitare i dati che verranno aggiunti a questo evento.
1. Fai clic su **[!UICONTROL Keep Changes]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che le estensioni ascoltino l&#39;evento.

Nell&#39;esempio seguente, `poiCity` e `poiName` i valori vengono aggiunti alla **[!UICONTROL mboxparameters]** per ogni richiesta elaborata nell&#39;evento Target. I valori per le nuove chiavi sono determinati dinamicamente dall&#39;SDK al momento dell&#39;elaborazione dell&#39;evento.

>[!TIP]
>
>Questo payload JSON utilizza una notazione speciale per l&#39; `request` oggetto. Nell&#39;evento originale, `request` è un array di oggetti anonimi. Quando si associano dati a tutti gli oggetti di una matrice utilizzando l&#39;opzione Allega dati, la `[*]` notazione di una chiave che contiene una matrice determina l&#39;applicazione del payload a tutti gli oggetti della matrice.
>
>La notazione di `request[*]` può essere letta a voce alta come _per ogni oggetto dell&#39;`request`array_.

![definire l&#39;azione](/help/assets/ad-setAction-target.png)

## 5. Salvate la regola e ricreate la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l&#39;aspetto seguente:

![regola completata](/help/assets/ad-ruleComplete-target.png)

1. Fai clic su **[!UICONTROL Save]**.
1. Generate di nuovo la proprietà Launch e distribuitela nell&#39;ambiente corretto.
