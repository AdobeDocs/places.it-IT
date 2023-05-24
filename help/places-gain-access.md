---
title: Accedere a Places Service
description: In questa sezione vengono fornite informazioni su come aggiungere un utente a Places Service e Experience Platform Launch, in modo che possa accedere a Places Service.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Accedere a Places Service {#adding-user-launch-places}

Places Service è ora disponibile all’interno dell’interfaccia utente di Data Collection. Puoi accedere a Raccolta dati dal menu di accesso rapido su [Pagina principale di Adobe Experience Cloud](https://experience.adobe.com).

![menu di accesso rapido](/help/assets/quickaccess.png)

Puoi accedere a Raccolta dati anche dal menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se il tuo ID utente dispone dell’accesso, visualizzerai l’icona Places Service nel pannello a sinistra in Gestione dati in Raccolta dati come indicato di seguito:

![Pannello sinistro della raccolta dati](/help/assets/places_in_data_collection.png)

Se il servizio Places non è disponibile in questa posizione, contatta un amministratore della tua organizzazione per aggiungere l’ID utente a Adobe Experience Platform nell’Admin Console.

## Aggiunta di un utente per accedere al servizio Places e alla raccolta dati di Experience Adobe Experience Platform

Places è ora incluso in Adobe Experience Platform. Per consentire agli utenti di accedere al [Places Service](https://experience.adobe.com/#/data-collection/places), devono essere aggiunte a Adobe Experience Platform nell’Admin Console come utente. Per consentire agli utenti di accedere alla raccolta dati di Experience Platform con le autorizzazioni necessarie per configurare le proprietà dei dispositivi mobili e utilizzare Places con l’SDK di Adobe Experience Platform, è necessario aggiungerli anche alla raccolta dati di Adobe Experience Platform nell’Admin Console e ottenere le seguenti autorizzazioni per la raccolta dati di Adobe Experience Platform:

* Tutte le autorizzazioni in Diritti di proprietà:
   * Approvazione
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

1. Accedi all’organizzazione Experience Cloud, [Pagina principale di Adobe Experience Cloud](https://experience.adobe.com).
1. In alto a destra, fai clic sul selettore della shell di Experience Cloud per visualizzare un menu a discesa.

   ![commutatore shell](/help/assets/places_shell_switcher1.png)

1. Nella parte inferiore dell’elenco, fai clic su **[!UICONTROL Admin Console]**. (Un collegamento al **[!UICONTROL Admin Console]** si trova anche nella sezione Accesso rapido).

   Se non vede **[!UICONTROL Admin Console]** nell’elenco, non sei un amministratore. Per completare questa procedura, contatta l’amministratore dell’organizzazione.

1. Nell’Admin Console, se hai accesso a più organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l’organizzazione a cui aggiungerai gli utenti. Se non è stata selezionata l’organizzazione corretta, fai clic sull’organizzazione e seleziona quella corretta dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se l’organizzazione desiderata non è presente nell’elenco a discesa, significa che non disponi dell’accesso come amministratore per tale organizzazione.

1. Nell’Admin Console, fai clic sulla scheda Prodotti e verifica che le schede per **[!UICONTROL Raccolta dati di Adobe Experience Platform]** e **[!UICONTROL Adobe Experience Platform]** vengono visualizzati.

   ![](/help/assets/places_provisioned1.png)

   Il provisioning di questi 2 prodotti viene eseguito automaticamente per tutte le organizzazioni, pertanto devono essere presenti.


### 2. Aggiungere un utente a questi prodotti

#### Aggiungere un utente per fornire l’accesso all’interfaccia utente di Places Service

1. Dalla scheda Prodotti, fai clic su **[!UICONTROL Adobe Experience Platform]** Card.
2. Un utente può essere aggiunto a qualsiasi profilo in **[!UICONTROL Adobe Experience Platform]** per accedere a Places non è necessario impostare autorizzazioni specifiche.
3. Scegli un profilo (se ne esiste più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul pulsante blu **Aggiungi utente** , compila l’utente con il relativo Adobe ID e nome, quindi fai clic su Salva per completare l’aggiunta.

#### Aggiungere un utente alla raccolta dati

1. Dalla scheda Prodotti, fai clic su **[!UICONTROL Raccolta dati di Adobe Experience Platform]** Card.
2. Per impostazione predefinita, un profilo denominato **Accesso predefinito a tutti i tipi di raccolta dati** sarà stato creato. L’aggiunta di un utente a questo profilo garantirà che disponga delle autorizzazioni appropriate per lavorare con Places Service e Data Collection. Se viene scelto un profilo diverso, accertati di includere le autorizzazioni menzionate in precedenza.
3. Scegli un profilo (se ne esiste più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul pulsante blu **Aggiungi utente** , compila l’utente con il relativo Adobe ID e nome, quindi fai clic su Salva per completare l’aggiunta.

#### Aggiungi un utente come sviluppatore per Places Service.

Per gli utenti che hanno bisogno di accedere anche all’API REST di Places Service, devi aggiungerli come sviluppatore.
1. Dalla scheda Prodotti, fai clic su **[!UICONTROL Adobe Experience Platform]** Card.
2. Se l’utente è già stato aggiunto a **[!UICONTROL Adobe Experience Platform]** tramite le istruzioni precedenti, scegli lo stesso profilo utilizzato in precedenza e fai clic su di esso.
3. All’interno del profilo, fai clic su **Sviluppatori** scheda
4. Fai clic sul pulsante blu **Aggiungi sviluppatore** , compila l’utente con il relativo Adobe ID e nome, quindi fai clic su Salva per completare l’aggiunta.

Dopo aver completato i passaggi precedenti, l’utente riceverà un’e-mail che gli notifica l’accesso a **[!UICONTROL Adobe Experience Platform]** e **[!UICONTROL Raccolta dati di Adobe Experience Platform]**. Potranno quindi accedere a [Adobe Experience Cloud](https://experience.adobe.com) per questa organizzazione e accedi al servizio Places e alla raccolta dati. Se completi anche i passaggi **[!UICONTROL Aggiungi uno sviluppatore]**, l&#39;utente può anche accedere a [Console Adobe Developer](https://developer.adobe.com/console/home) per creare un progetto che fornisca l’accesso all’API REST di Places Service.
