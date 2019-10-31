---
title: Adobe Target
seo-title: Adobe Target
description: Questa sezione fornisce informazioni sull'utilizzo di Location Service con Adobe Target.
seo-description: 'Questa sezione fornisce informazioni sull''utilizzo di Location Service con Adobe Target. '
translation-type: tm+mt
source-git-commit: 7ca51580a4cfa9c00431ad3972bd10e2a12dfbd1

---


# Adobe Target {#places-target}

In questo documento si presuppone che l'estensione Luoghi sia stata implementata nell'applicazione. Per assistenza nell'implementazione dell'estensione Luoghi, vedere Estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

Dopo che l'estensione Luoghi invia eventi per voci ed uscite, puoi utilizzare Regole in Launch per allegare i dati Luoghi agli eventi SDK di Adobe Target. Con la proprietà desiderata selezionata in Lancio, potete creare questo tipo di regola completando le seguenti attività:

## 1. Creare una regola

1. Nella **[!UICONTROL Rules]** scheda fare clic su **[!UICONTROL Create New Rule]**.

   Considerazioni da ricordare:

   * Se non sono presenti regole per questa proprietà, il pulsante si trova al centro dello schermo.
   * Se la proprietà dispone di regole, il pulsante si trova in alto a destra nella schermata.

## 2. Selezionare un evento

1. Attribuite alla regola un nome significativo in modo che possa essere facilmente riconoscibile nell'elenco delle regole.

   In questo esempio, la regola viene denominata **[!UICONTROL Attach Places Data to Target Content Requested]**.

2. Nella **[!UICONTROL Events]** sezione fare clic su **[!UICONTROL Add]**.

3. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Adobe Target]**.

4. Dall’elenco a **[!UICONTROL Event Type]** discesa, selezionate **[!UICONTROL Content Requested]**.

5. Fai clic su **[!UICONTROL Keep Changes]**.

![aggiungere un evento](/help/assets/ad-setEvent_target.png)

## 3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio se desideri aggiungere Condizioni alla regola. In caso contrario, passare a *Definisci azione* .

Nell'esempio seguente, viene creata una condizione che determina l'attivazione della regola solo per gli utenti che hanno avviato l'app cinque o più volte.

1. Nella **[!UICONTROL Conditions]** sezione fare clic su **[!UICONTROL Add]**.

2. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.

3. Dall’elenco a **[!UICONTROL Condition Type]** discesa, selezionate **[!UICONTROL Launches]**.

4. Nel riquadro a destra, modificate l'elenco a discesa e i controlli numerici in modo che la condizione **[!UICONTROL User ha avviato l'app più o meno 5 volte**.

5. Fai clic su **[!UICONTROL Keep Changes]**.

![aggiungere un evento](/help/assets/ad-setCondition_target.png)

## 4. Definire l'azione

1. Nella **[!UICONTROL Actions]** sezione fare clic su **[!UICONTROL Add]**.

2. Dall’elenco a **[!UICONTROL Extension]** discesa, selezionate **[!UICONTROL Mobile Core]**.

3. Dall’elenco a **[!UICONTROL Action Type]** discesa, selezionate **[!UICONTROL Attach Data]**.

4. Nel riquadro di destra, nel **[!UICONTROL JSON Payload]** campo, digitare i dati che verranno aggiunti a questo evento.

5. Fai clic su **[!UICONTROL Keep Changes]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che le estensioni ascoltino l'evento.

Nell'esempio seguente, `poiCity` e `poiName` i valori vengono aggiunti alla **[!UICONTROL mboxparameters]** per ogni richiesta elaborata nell'evento Target. I valori delle nuove chiavi sono determinati dinamicamente dall'SDK al momento dell'elaborazione dell'evento.

>[!TIP
>]
>Questo payload JSON utilizza una notazione speciale per l' `request` oggetto. Nell'evento originale, `request` è un array di oggetti anonimi. Quando si associano dati a tutti gli oggetti di una matrice utilizzando l'opzione Allega dati, la `[*]` notazione di una chiave che contiene una matrice determina l'applicazione del payload a tutti gli oggetti della matrice.
>
>La notazione di `request[*]` può essere letta a voce alta come _per ogni oggetto dell' `request` array.

![aggiungere un evento](/help/assets/ad-setCondition_target.png)

## 5. Salvate la regola e ricreate la proprietà

Dopo aver completato la configurazione, verifica che la regola abbia l'aspetto seguente:

![regola completata](/help/assets/ad-ruleComplete_target.png)

1. Fai clic su **[!UICONTROL Save]**

2. Generate di nuovo la proprietà Launch e distribuitela nell'ambiente corretto.
