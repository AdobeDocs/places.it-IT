---
title: Accedere a Places Service
description: In questa sezione vengono fornite informazioni su come aggiungere un utente a Places Service e Experienci Platform Launch, in modo che possa accedere a Places Service.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Accedere a Places Service {#adding-user-launch-places}

Places Service è ora disponibile all’interno dell’interfaccia utente di Data Collection. Puoi accedere a Raccolta dati dal menu di accesso rapido nella [Home di Adobe Experience Cloud](https://experience.adobe.com).

![menu di accesso rapido](/help/assets/quickaccess.png)

Puoi accedere a Raccolta dati anche dal menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se il tuo ID utente dispone dell’accesso, visualizzerai l’icona Places Service nel pannello a sinistra in Gestione dati in Raccolta dati come indicato di seguito:

![Pannello sinistro raccolta dati](/help/assets/places_in_data_collection.png)

Se il servizio Places non è disponibile in questa posizione, contatta un amministratore della tua organizzazione per aggiungere l’ID utente a Adobe Experience Platform nell’Admin Console.

## Aggiunta di un utente per accedere al servizio Places e alla raccolta dati di Experience Adobe Experience Platform

Places è ora incluso in Adobe Experience Platform. Per consentire agli utenti di accedere al servizio [Places](https://experience.adobe.com/#/data-collection/places), è necessario aggiungerli a Adobe Experience Platform nell&#39;Admin Console come utente. Per consentire agli utenti di accedere alla raccolta dati di Experience Platform con le autorizzazioni necessarie per configurare le proprietà dei dispositivi mobili e utilizzare Places con l’SDK di Adobe Experience Platform, è necessario aggiungerli anche alla raccolta dati di Adobe Experience Platform nell’Admin Console e ottenere le seguenti autorizzazioni per la raccolta dati di Adobe Experience Platform:

* Tutte le autorizzazioni in Diritti di proprietà:
   * Approva
   * Sviluppa
   * Modifica proprietà
   * Gestisci ambienti
   * Gestire le estensioni
   * Pubblica
* Autorizzazione Gestione proprietà in Diritti aziendali

Se è la prima volta che aggiungi un utente, completa i passaggi seguenti per aggiungere utenti a Adobe Experience Platform Data Collection e Adobe Experience Platform. Se in precedenza hai aggiunto degli utenti, è possibile che vengano visualizzati più profili, quindi accertati di selezionare quello corretto.

>[!IMPORTANT]
>
>Solo gli amministratori dell’organizzazione possono accedere all’Admin Console e aggiungere gli utenti.

### 1. Verifica che sia stato eseguito il provisioning di Adobe Experience Platform e Adobe Experience Platform Data Collection

1. Accedi all&#39;organizzazione Experience Cloud, [Adobe Experience Cloud home](https://experience.adobe.com).
1. In alto a destra, fai clic sul selettore della shell di Experience Cloud per visualizzare un menu a discesa.

   ![commutatore shell](/help/assets/places_shell_switcher1.png)

1. Nella parte inferiore dell&#39;elenco fare clic su **[!UICONTROL Admin Console]**. (Un collegamento all&#39;**[!UICONTROL Admin Console]** è disponibile anche nella sezione Accesso rapido).

   Se non vedi **[!UICONTROL Admin Console]** nell&#39;elenco, non sei un amministratore. Per completare questa procedura, contatta l’amministratore dell’organizzazione.

1. Nell’Admin Console, se hai accesso a più organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l’organizzazione a cui aggiungerai gli utenti. Se non è stata selezionata l’organizzazione corretta, fai clic sull’organizzazione e seleziona quella corretta dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se l’organizzazione desiderata non è presente nell’elenco a discesa, significa che non disponi dell’accesso come amministratore per tale organizzazione.

1. Nell&#39;Admin Console, fare clic sulla scheda Prodotti e verificare che siano visualizzate le schede per **[!UICONTROL Raccolta dati Adobe Experience Platform]** e **[!UICONTROL Adobe Experience Platform]**.

   ![](/help/assets/places_provisioned1.png)

   Il provisioning di questi 2 prodotti viene eseguito automaticamente per tutte le organizzazioni, pertanto devono essere presenti.


### 2. Aggiungere un utente a questi prodotti

#### Aggiungere un utente per fornire l’accesso all’interfaccia utente di Places Service

1. Dalla scheda Prodotti, fai clic sulla scheda **[!UICONTROL Adobe Experience Platform]**.
2. È possibile aggiungere un utente a qualsiasi profilo all&#39;interno di **[!UICONTROL Adobe Experience Platform]** per accedere a Places. Non è necessario impostare autorizzazioni specifiche.
3. Scegli un profilo (se ne esiste più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul pulsante blu **Aggiungi utente**, inserisci l&#39;utente con il relativo Adobe ID e nome, quindi fai clic su Salva per completare l&#39;aggiunta.

#### Aggiungere un utente alla raccolta dati

1. Dalla scheda Prodotti, fai clic sulla scheda **[!UICONTROL Raccolta dati di Adobe Experience Platform]**.
2. Per impostazione predefinita, verrà creato un profilo denominato **Raccolta dati predefinita, Accesso completo**. L’aggiunta di un utente a questo profilo garantirà che disponga delle autorizzazioni appropriate per lavorare con Places Service e Data Collection. Se viene scelto un profilo diverso, accertati di includere le autorizzazioni menzionate in precedenza.
3. Scegli un profilo (se ne esiste più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul pulsante blu **Aggiungi utente**, inserisci l&#39;utente con il relativo Adobe ID e nome, quindi fai clic su Salva per completare l&#39;aggiunta.

#### Aggiungi un utente come sviluppatore per Places Service.

Per gli utenti che hanno bisogno di accedere anche all’API REST di Places Service, devi aggiungerli come sviluppatore.
1. Dalla scheda Prodotti, fai clic sulla scheda **[!UICONTROL Adobe Experience Platform]**.
2. Se l&#39;utente è già stato aggiunto alla scheda **[!UICONTROL Adobe Experience Platform]** tramite le istruzioni precedenti, scegliere lo stesso profilo utilizzato in precedenza e fare clic su di esso.
3. Nel profilo, fai clic sulla scheda **Sviluppatori**
4. Fai clic sul pulsante blu **Aggiungi sviluppatore**, inserisci l&#39;utente con il suo Adobe ID e nome, quindi fai clic su Salva per completare l&#39;aggiunta.

Dopo aver completato i passaggi precedenti, l&#39;utente riceverà un&#39;e-mail con la notifica di poter accedere a **[!UICONTROL Adobe Experience Platform]** e **[!UICONTROL Raccolta dati di Adobe Experience Platform]**. Potranno quindi accedere a [Adobe Experience Cloud](https://experience.adobe.com) per questa organizzazione e accedere a Places Service e Data Collection. Se si completa anche la procedura **[!UICONTROL Aggiungi uno sviluppatore]**, l&#39;utente può accedere anche a [Adobe Developer Console](https://developer.adobe.com/console/projects) per creare un progetto che fornisca l&#39;accesso all&#39;API REST di Places Service.
