---
title: Accesso al servizio Places
description: Questa sezione fornisce informazioni su come aggiungere un utente a Places Service e Experience Platform Launch, in modo che l’utente possa accedere a Places Service.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Accesso al servizio Places {#adding-user-launch-places}

Il servizio Places è ora disponibile nell’interfaccia utente di raccolta dati. Puoi accedere a Raccolta dati dal menu di accesso rapido disponibile in [Pagina principale di Adobe Experience Cloud](https://experience.adobe.com).

![menu di accesso rapido](/help/assets/quickaccess.png)

Puoi anche accedere a Raccolta dati dal menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se il tuo ID utente ha accesso, vedrai l’icona del servizio Luoghi nel pannello a sinistra in Gestione dati nella raccolta dati come indicato di seguito:

![Pannello a sinistra della raccolta dati](/help/assets/places_in_data_collection.png)

Se il servizio Places non è presente in questa posizione, contatta un amministratore dell’organizzazione per aggiungere l’ID utente a Adobe Experience Platform nell’Admin Console.

## Aggiunta di un utente per accedere al servizio Places e alla raccolta dati di Experience Adobe Experience Platform

Luoghi è ora incluso in Adobe Experience Platform. Per consentire agli utenti di accedere al [Places Service](https://experience.adobe.com/#/data-collection/places), devono essere aggiunti a Adobe Experience Platform nell’Admin Console come utente. Per consentire agli utenti di accedere ad Experience Platform Data Collection con le autorizzazioni necessarie per configurare le proprietà mobili e utilizzare Places con Adobe Experience Platform SDK, è necessario aggiungere gli utenti a Adobe Experience Platform Data Collection nell’Admin Console e ottenere le seguenti autorizzazioni per Adobe Experience Platform Data Collection:

* Tutte le autorizzazioni in Diritti di proprietà:
   * Approva
   * Sviluppa
   * Modifica, proprietà
   * Gestire gli ambienti
   * Gestire le estensioni
   * Pubblica
* Gestisci autorizzazioni proprietà in Diritti aziendali

Se questa è la prima volta che aggiungi un utente, completa i passaggi seguenti per aggiungere utenti a Adobe Experience Platform Data Collection e Adobe Experience Platform. Se hai aggiunto utenti in precedenza, potrebbero essere visualizzati più profili, in modo da assicurarti di selezionare il profilo corretto.

>[!IMPORTANT]
>
>Solo gli amministratori dell’organizzazione possono accedere all’Admin Console e aggiungere gli utenti.

### 1. Verifica che sia stato eseguito il provisioning della raccolta dati di Adobe Experience Platform e Adobe Experience Platform

1. Accedi alla tua organizzazione Experience Cloud, [Pagina principale di Adobe Experience Cloud](https://experience.adobe.com).
1. In alto a destra, fai clic sul commutatore della shell Experience Cloud per visualizzare un menu a discesa.

   ![commutatore a guscio](/help/assets/places_shell_switcher1.png)

1. In fondo all’elenco, fai clic su **[!UICONTROL Admin Console]**. (Un collegamento alla **[!UICONTROL Admin Console]** si trova anche nella sezione Accesso rapido ).

   Se non vedi **[!UICONTROL Admin Console]** nell’elenco, non sei un amministratore. Per completare questa procedura, contatta l’amministratore organizzazione.

1. Nell’Admin Console, se disponi dell’accesso a diverse organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l’organizzazione a cui verranno aggiunti gli utenti. Se l’organizzazione corretta non è stata selezionata, fai clic sull’organizzazione e seleziona l’organizzazione corretta dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se l’organizzazione desiderata non si trova nell’elenco a discesa, significa che non disponi dell’accesso amministratore a tale organizzazione.

1. Nell’Admin Console, fai clic sulla scheda Prodotti e verifica che le schede per **[!UICONTROL Raccolta dati Adobe Experience Platform]** e **[!UICONTROL Adobe Experience Platform]** vengono visualizzati.

   ![](/help/assets/places_provisioned1.png)

   Questi 2 prodotti vengono automaticamente forniti a tutte le organizzazioni, quindi dovrebbero essere presenti.


### 2. Aggiungi utente a questi prodotti

#### Aggiungi l’utente per fornire accesso all’interfaccia utente di Places Service

1. Dalla scheda Prodotti , fai clic sul pulsante **[!UICONTROL Adobe Experience Platform]** il Card.
2. Un utente può essere aggiunto a qualsiasi profilo all’interno di **[!UICONTROL Adobe Experience Platform]** per accedere a Luoghi, non è necessario impostare autorizzazioni specifiche.
3. Scegli un profilo (se ce n&#39;è più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul blu **Aggiungi utente** , compila l’utente con il suo Adobe ID e il suo nome, quindi fai clic su Salva per completare l’aggiunta.

#### Aggiungi utente alla raccolta dati

1. Dalla scheda Prodotti , fai clic sul pulsante **[!UICONTROL Raccolta dati Adobe Experience Platform]** il Card.
2. Per impostazione predefinita, un profilo denominato **Accesso completo alla raccolta dati predefinita** sarà stato creato. L’aggiunta di un utente a questo profilo garantirà che disponga delle autorizzazioni appropriate per lavorare con il servizio Places e la raccolta dati. Se selezioni un profilo diverso, assicurati che le autorizzazioni siano incluse come indicato in precedenza.
3. Scegli un profilo (se ce n&#39;è più di uno) e fai clic su di esso per aprirlo.
4. Fai clic sul blu **Aggiungi utente** , compila l’utente con il suo Adobe ID e il suo nome, quindi fai clic su Salva per completare l’aggiunta.

#### Aggiungi un utente come sviluppatore per Places Service.

Per gli utenti che necessitano anche dell’accesso all’API REST di Places Service, è necessario aggiungerli come sviluppatori.
1. Dalla scheda Prodotti , fai clic sul pulsante **[!UICONTROL Adobe Experience Platform]** il Card.
2. Se l’utente è già stato aggiunto a **[!UICONTROL Adobe Experience Platform]** tramite le istruzioni di cui sopra, scegli lo stesso profilo utilizzato in precedenza e fai clic su di esso.
3. All’interno del profilo, fai clic sul pulsante **Sviluppatori** scheda
4. Fai clic sul blu **Aggiungi sviluppatore** , compila l’utente con il suo Adobe ID e il suo nome, quindi fai clic su Salva per completare l’aggiunta.

Dopo aver completato i passaggi precedenti, l’utente riceverà un’e-mail con la notifica di accesso a **[!UICONTROL Adobe Experience Platform]** e **[!UICONTROL Raccolta dati Adobe Experience Platform]**. Possono quindi accedere al [Adobe Experience Cloud](https://experience.adobe.com) per questa organizzazione e accedi a Places Service e Data Collection. Se completi anche i passaggi **[!UICONTROL Aggiungi uno sviluppatore]**, l’utente può anche accedere al [Console Adobe Developer](https://developer.adobe.com/console/home) per creare un progetto che fornisca l’accesso all’API REST del servizio Places.
