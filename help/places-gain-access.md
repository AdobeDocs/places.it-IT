---
title: 'Accesso ai servizi Places '
description: Questa sezione fornisce informazioni su come aggiungere un utente al servizio Places e al lancio della piattaforma Experience, in modo che l'utente possa accedere al servizio Places.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---

# Accesso ai servizi Places {#adding-user-launch-places}

Puoi accedere al servizio Luoghi dal menu di accesso rapido nella home [di](https://experience.adobe.com)Adobe Experience Cloud.
Se l’ID utente dispone dell’accesso, verrà visualizzata l’icona del servizio Luoghi come indicato di seguito:

![menu di accesso rapido](/help/assets/quick-access.png)

Puoi anche accedere al servizio Places dal menu Adobe Experience Platform:

![Menu della piattaforma Experience](/help/assets/exp-platform-menu-sm.png)

Se non trovi il servizio Luoghi in uno di questi menu, contatta un amministratore della tua organizzazione per aggiungere il tuo ID utente al servizio di base Luoghi in Admin Console.

## Aggiunta di un utente al servizio Places e al lancio della piattaforma Experience

Per consentire agli utenti di accedere all’interfaccia utente [di avvio della piattaforma](https://launch.adobe.com)Experience, è necessario aggiungerli al servizio di base Places nell’Admin Console come utente. Per consentire agli utenti di accedere a Experience Platform Launch, configurare le proprietà dei dispositivi mobili e utilizzare Places con l’SDK di Adobe Experience Platform, è necessario aggiungerli ad Experience Platform Launch nell’Admin Console e ottenere le seguenti autorizzazioni per Experience Platform Launch:

* Tutti i diritti di proprietà:
   * Develop
   * Approva
   * Pubblica
   * Gestire le estensioni
   * Gestione degli ambienti
* Autorizzazione Gestisci proprietà in Diritti aziendali

Se si tratta della prima volta che aggiungete un utente, completate i seguenti passaggi per aggiungere utenti al servizio Experience Platform Launch e Places. Se avete già aggiunto degli utenti, potrebbero essere visualizzati più profili, in modo da assicurarvi di selezionare il profilo corretto.

>[!IMPORTANT]
>
>Solo gli amministratori dell&#39;organizzazione possono accedere ad Admin Console e aggiungere gli utenti.

### 1. Verifica che sia stato eseguito il provisioning di Servizio Places e di Avvio della piattaforma Experience

1. Accedi alla tua organizzazione Experience Cloud.
1. In alto a destra, fai clic sul commutatore di shell Experience Cloud.

   ![commutatore shell](/help/assets/places_shell_switcher1.png)

1. Alla voce **[!UICONTROL Platform]**, fai clic su**[!UICONTROL Administration]**.

   Se nell’elenco non è presente **Amministrazione** , non si è un amministratore. Per completare questa procedura, è necessario contattare l’amministratore dell’organizzazione.

1. Nella pagina Amministrazione di Experience Cloud, sulla **[!UICONTROL Admin Console]**scheda, fai clic su**[!UICONTROL Take me there]**.

1. In Admin Console, se hai accesso a diverse organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l&#39;organizzazione a cui aggiungerete i vostri utenti. Se l’organizzazione corretta non è stata selezionata, fate clic sull’organizzazione e selezionate l’organizzazione dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se non avete accesso a un&#39;organizzazione, significa che non disponete dell&#39;accesso dell&#39;amministratore a tale organizzazione.

1. Verify that the cards for **[!UICONTROL Adobe Experience Platform Launch]**and**[!UICONTROL Places Core Services]** are displayed.

   ![](/help/assets/places_provisioned1.png)

   Se visualizzati, sono stati forniti i servizi Luoghi e il lancio della piattaforma Esperienza per la vostra organizzazione. Se non vengono visualizzati, è necessario fornire il provisioning per l&#39;organizzazione.


### 2. Configurare il profilo e aggiungere le autorizzazioni

1. Configurate un profilo Experience Platform Launch che consente agli utenti aggiunti al profilo di utilizzare Experience Platform Launch e le relative proprietà mobili con l’SDK di Experience Platform.

   a. Nella barra dei menu, fate clic su **[!UICONTROL Product]**.

   b. Nel riquadro a sinistra, nell’elenco dei prodotti, fate clic su **[!UICONTROL Adobe Experience Platform Launch]**.

   * I profili di Launch della piattaforma Experience appaiono a destra.
   * Experience Platform Launch ha un profilo predefinito chiamato *Launch - (nome organizzazione)* .

      Se in precedenza hai aggiunto utenti a Experience Platform Launch, potrebbero essere elencati più profili.

1. Seleziona il profilo corretto:

   a. Fare clic sul nome del profilo predefinito.

   b. Fate clic sulla **[!UICONTROL Permissions]**scheda.

   c. Fate clic su **[!UICONTROL Edit]**accanto a**[!UICONTROL Property Rights]**.

   d. Nel riquadro a sinistra, fare clic su **[!UICONTROL + Add all]**.

   Questo passaggio sposta tutte le autorizzazioni disponibili nell&#39;elenco delle autorizzazioni incluse.

   e. Fate clic **[!UICONTROL Company Rights]**.

   f. Nel riquadro a sinistra, fare clic su **[!UICONTROL + Manage Properties]**.

   g. Fate clic **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Per il servizio Luoghi esiste un profilo predefinito, ma non è necessario aggiungere alcuna autorizzazione.

Sono state aggiunte le autorizzazioni al profilo creato.

### 3. Aggiungere un utente o uno sviluppatore ai profili di avvio di Servizio Places e Piattaforma esperienza

Puoi aggiungere un utente e/o uno sviluppatore ai profili di avvio del servizio Places e della piattaforma Experience.

### Aggiungere un utente

Per aggiungere un utente ai profili di avvio di Servizio Places e Piattaforma esperienza:

1. Aggiungi un utente al profilo Experience Platform Launch.

   a. Nella barra dei menu, fate clic su **[!UICONTROL Overview]**.

   b. Nella **[!UICONTROL Adobe Experience Platform Launch]**scheda, verificate quanto segue:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Il punto a sinistra è nero.

      Se il punto a destra è nero, potete aggiungere solo sviluppatori. Per aggiungere un utente, fate clic sul punto a sinistra.
   c. Fate clic **[!UICONTROL + Add Users]**.

   d. Immettete l’Adobe ID dell’utente.

   e. Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic **[!UICONTROL New user]**e immettete il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.
   f. Nell’elenco a **[!UICONTROL Please select a profile for this product]**discesa, selezionate il profilo modificato in precedenza.

   g. Fate clic **[!UICONTROL Save]**.

1. Aggiungete un utente a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Al momento, tutti gli utenti del servizio Luoghi dispongono delle stesse autorizzazioni, pertanto non è necessario modificare le autorizzazioni.

   a. Nella **[!UICONTROL Places Core Services]**scheda, verificate quanto segue:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Il punto a sinistra è nero.
   b. Fate clic **[!UICONTROL + Assign Users]**.

   c. Immettete l’Adobe ID dell’utente.

   d. Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic **[!UICONTROL New user]**e immettete il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.
   e. Nell&#39;elenco a **[!UICONTROL Please select a profile for this product]**discesa, selezionare il profilo Luoghi.

   f. Fate clic **[!UICONTROL Save]**.

### Aggiunta di uno sviluppatore

Per gli utenti che necessitano anche dell&#39;accesso a Web Service API, è necessario aggiungerli come sviluppatore.

Per aggiungere uno sviluppatore:

1. On the **[!UICONTROL Places Core Services]**card, verify the following:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Fate clic sul punto a destra in modo che **[!UICONTROL Assign Developers]**venga visualizzato nella parte inferiore della scheda.

1. Fai clic su **[!UICONTROL + Assign Developers]**.

1. Inserisci l’Adobe ID dell’utente.

1. Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic su di esso **[!UICONTROL New user]**e inserite il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.

1. Nell&#39;elenco a **[!UICONTROL Please select a profile for this product]**discesa, selezionare il profilo Luoghi di assistenza.

1. Fai clic su **Salva**.

Gli utenti ricevono un messaggio e-mail con la conferma di accesso a Experience Platform Launch. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Se completi il passaggio 4 della procedura **Aggiungi gli sviluppatori**, l’utente può accedere anche alla [console Adobe I/O](https://console.adobe.io) per creare un’integrazione di Luoghi e utilizzare l’API REST Luoghi.
