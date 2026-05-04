---
title: Adobe Target
description: Questa sezione fornisce informazioni sull’utilizzo di Places Service con Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
TQID: https://experienceleague.adobe.com/WsfkEJD0mN5aYKETjcnqiC13dVe5NPYeKfOCTOK82uE
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 2%

---

# Utilizzare Places Service con Adobe Target {#places-target}

In questo documento si presuppone che sia stata implementata l’estensione Places nell’applicazione. Se hai bisogno di aiuto per implementare l&#39;estensione Luoghi, consulta [Estensioni Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Dopo che l’estensione Luoghi invia eventi per le entrate e le uscite, puoi sfruttare le Regole in Launch per allegare i dati di Places Service agli eventi di Adobe Target SDK. Con la proprietà desiderata selezionata in Launch, puoi creare questo tipo di regola completando le seguenti attività:

## &#x200B;1. Creare una regola

1. Nella scheda **[!UICONTROL Regole]**, fai clic su **[!UICONTROL Crea nuova regola]**.

   Considerazioni da ricordare:

   * Se non disponi di regole esistenti per questa proprietà, il pulsante si trova al centro della schermata.
   * Se la proprietà dispone di regole, il pulsante si trova in alto a destra dello schermo.

## &#x200B;2. Seleziona un evento

1. Assegna alla regola un nome significativo in modo che sia facilmente riconoscibile nell’elenco delle regole.

   In questo esempio, la regola è denominata **[!UICONTROL Allega dati del servizio Places al contenuto di destinazione richiesto]**.

1. Nella sezione **[!UICONTROL Events]**, fai clic su **[!UICONTROL Add]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, selezionare **[!UICONTROL Adobe Target]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Tipo evento]**, selezionare **[!UICONTROL Contenuto richiesto]**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

![aggiungi un evento](/help/assets/ad-setEvent_target.png)

## &#x200B;3. Aggiungi condizioni

>[!IMPORTANT]
>
>Completa questo passaggio se desideri aggiungere Condizioni alla regola. In caso contrario, passa a *Definisci l&#39;azione* di seguito.

Nell’esempio seguente, viene creata una condizione per cui la regola viene attivata solo per gli utenti che hanno avviato l’app cinque o più volte.

1. Nella sezione **[!UICONTROL Conditions]**, fai clic su **[!UICONTROL Add]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Tipo di condizione]**, selezionare **[!UICONTROL Avvii]**.
1. Nel riquadro di destra, modificare l&#39;elenco a discesa e i controlli numerici in modo che la condizione indichi **[!UICONTROL L&#39;utente ha avviato l&#39;app più o meno di 5 volte]**.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

![aggiungi una condizione](/help/assets/ad-setCondition_target.png)

## &#x200B;4. Definire l’azione

1. Nella sezione **[!UICONTROL Azioni]**, fai clic su **[!UICONTROL Aggiungi]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Estensione]**, seleziona **[!UICONTROL Mobile Core]**.
1. Dall&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Allega dati]**.
1. Nel riquadro di destra, nel campo **[!UICONTROL Payload JSON]**, digitare i dati che verranno aggiunti a questo evento.
1. Fai clic su **[!UICONTROL Mantieni modifiche]**.

Nel riquadro a destra, puoi aggiungere un payload JSON a forma libera che aggiunge dati a un evento SDK prima che le estensioni in ascolto di questo evento lo udano.

Nell&#39;esempio seguente, i valori `poiCity` e `poiName` vengono aggiunti ai **[!UICONTROL mboxparameters]** per ogni richiesta elaborata nell&#39;evento Target. I valori per le nuove chiavi vengono determinati dinamicamente da SDK al momento dell’elaborazione di questo evento.

>[!TIP]
>
>Questo payload JSON utilizza una notazione speciale per l&#39;oggetto `request`. Nell&#39;evento originale, `request` è un array di oggetti anonimi. Quando si allegano dati a tutti gli oggetti di un array utilizzando l&#39;opzione Allega dati, la notazione `[*]` su una chiave che contiene un array determina l&#39;applicazione del payload a tutti gli oggetti dell&#39;array.
>
>La notazione di `request[*]` può essere letta ad alta voce come _per ogni oggetto nell&#39;array `request`_.

![definire l&#39;azione](/help/assets/ad-setAction-target.png)

## &#x200B;5. Salvare la regola e ricreare la proprietà

Dopo aver completato la configurazione, verifica che la regola sia simile alla seguente immagine:

![regola completata](/help/assets/ad-ruleComplete-target.png)

1. Fai clic su **[!UICONTROL Salva]**
1. Rigenera la proprietà Launch e distribuiscila nell’ambiente corretto.
