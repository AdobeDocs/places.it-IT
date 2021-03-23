---
title: 'Accesso al servizio Places '
description: Questa sezione fornisce informazioni su come aggiungere un utente a Places Service e Experience Platform Launch, in modo che l’utente possa accedere a Places Service.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 9%

---

# Accesso al servizio Places {#adding-user-launch-places}

È possibile accedere al Servizio Luoghi dal menu di accesso rapido in [Adobe Experience Cloud home](https://experience.adobe.com).
Se l’ID utente dispone dell’accesso, verrà visualizzata l’icona del servizio Places come indicato di seguito:

![menu di accesso rapido](/help/assets/quickaccess.png)

È inoltre possibile accedere a Places Service dal menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se il servizio Places non è presente in nessuno di questi menu, contatta un amministratore dell’organizzazione per aggiungere l’ID utente al servizio core Places nell’Admin Console.

## Aggiunta di un utente al servizio e al Experience Platform Launch Places

Per consentire agli utenti di accedere all’ [interfaccia utente del Experience Platform Launch](https://launch.adobe.com), è necessario aggiungerli al servizio core Places nell’Admin Console come utente. Per consentire agli utenti di accedere al Experience Platform Launch, configurare le proprietà mobile e utilizzare Luoghi con l’SDK di Adobe Experience Platform, è necessario aggiungerli al Experience Platform Launch nell’Admin Console e ottenere, ad Experience Platform Launch, le seguenti autorizzazioni:

* Tutti i diritti di proprietà:
   * Sviluppa
   * Approva
   * Pubblica
   * Gestire le estensioni
   * Gestire gli ambienti
* Gestisci autorizzazioni proprietà in Diritti aziendali

Se questa è la prima volta che aggiungi un utente, completa i passaggi seguenti per aggiungere utenti a Experience Platform Launch e Places Service. Se hai aggiunto utenti in precedenza, potrebbero essere visualizzati più profili, in modo da assicurarti di selezionare il profilo corretto.

>[!IMPORTANT]
>
>Solo gli amministratori dell’organizzazione possono accedere all’Admin Console e aggiungere gli utenti.

### 1. Verifica che sia stato eseguito il provisioning di Places Service e Experience Platform Launch

1. Accedi alla tua organizzazione Experience Cloud.
1. In alto a destra, fai clic sul commutatore della shell di Experience Cloud.

   ![commutatore a guscio](/help/assets/places_shell_switcher1.png)

1. In **[!UICONTROL Piattaforma]**, fai clic su **[!UICONTROL Amministrazione]**.

   Se non trovi **[!UICONTROL Amministrazione]** nell&#39;elenco, non sei un amministratore. Per completare questa procedura, contatta l’amministratore organizzazione.

1. Nella pagina Amministrazione Experience Cloud, nella scheda **[!UICONTROL Admin Console]**, fai clic su **[!UICONTROL Portami lì]**.

1. Nell’Admin Console, se disponi dell’accesso a diverse organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l’organizzazione a cui verranno aggiunti gli utenti. Se l’organizzazione corretta non è stata selezionata, fai clic sull’organizzazione e selezionala dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se non hai accesso a un&#39;organizzazione, significa che non hai accesso come amministratore a tale organizzazione.

1. Verifica che siano visualizzate le schede per **[!UICONTROL Adobe Experience Platform Launch]** e **[!UICONTROL Places Core Services]**.

   ![](/help/assets/places_provisioned1.png)

   Se vengono visualizzati, è stato effettuato il provisioning di Places Service e Experience Platform Launch per la tua organizzazione. Se non vengono visualizzati, è necessario eseguirne il provisioning per la tua organizzazione.


### 2. Imposta il profilo e aggiungi le autorizzazioni

1. Imposta un profilo di Experience Platform Launch, che consente agli utenti che sono stati aggiunti al profilo di utilizzare il Experience Platform Launch e le relative proprietà mobili con l’SDK di Experience Platform.

   a) Nella barra dei menu, fai clic su **[!UICONTROL Prodotto]**.

   b) Nel riquadro a sinistra, nell&#39;elenco dei prodotti, fai clic su **[!UICONTROL Adobe Experience Platform Launch]**.

   * I profili di Experience Platform Launch vengono visualizzati a destra.
   * Il profilo predefinito del Experience Platform Launch è *Launch - (nome organizzazione)* .

      Se in precedenza hai aggiunto utenti al Experience Platform Launch, potrebbero essere elencati più profili.

1. Seleziona il profilo corretto:

   a) Fai clic sul nome del profilo predefinito.

   b) Fare clic sulla scheda **[!UICONTROL Autorizzazioni]**.

   c. Fai clic su **[!UICONTROL Modifica]** accanto a **[!UICONTROL Property Rights]** (Diritti di proprietà).

   d. Nel riquadro a sinistra, fai clic su **[!UICONTROL + Aggiungi tutto]**.

   Questo passaggio sposta tutte le autorizzazioni disponibili nell&#39;elenco delle autorizzazioni incluse.

   e. Fai clic su **[!UICONTROL Diritti aziendali]**.

   f. Nel riquadro a sinistra, fai clic su **[!UICONTROL + Gestisci proprietà]**.

   g. Fai clic su **[!UICONTROL Salva]**.

>[!IMPORTANT]
>
>Per il servizio Places è presente un profilo predefinito, ma non è necessario aggiungere autorizzazioni.

Sono state aggiunte le autorizzazioni al profilo creato.

### 3. Aggiungi un utente o uno sviluppatore ai profili Places Service e Experience Platform Launch

Puoi aggiungere un utente e/o uno sviluppatore ai profili Places Service e Experience Platform Launch.

### Aggiungi un utente

Per aggiungere un utente al servizio Places e ai profili di Experience Platform Launch:

1. Aggiungi un utente al profilo di Experience Platform Launch.

   a) Nella barra dei menu, fai clic su **[!UICONTROL Panoramica]**.

   b) Nella scheda **[!UICONTROL Adobe Experience Platform Launch]** , verifica quanto segue:

   * Nella parte inferiore della scheda vengono visualizzati due punti.
   * Il punto a sinistra è nero.

      Se il punto a destra è nero, puoi aggiungere solo sviluppatori. Per aggiungere un utente, fai clic sul punto a sinistra.
   c. Fai clic su **[!UICONTROL + Aggiungi utenti]**.

   d. Immetti l’Adobe ID dell’utente.

   e. Completa uno dei seguenti passaggi:

   * Se si aggiunge un nuovo utente, fare clic su **[!UICONTROL Nuovo utente]** e immettere il nome e il cognome dell&#39;utente.
   * Se aggiungi un utente esistente, fai clic sul nome dell’utente visualizzato.

   f. Nell&#39;elenco a discesa **[!UICONTROL Selezionare un profilo per questo prodotto]**, selezionare il profilo modificato in precedenza.

   g. Fai clic su **[!UICONTROL Salva]**.

1. Aggiungi un utente a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Attualmente, tutti gli utenti del servizio Places dispongono delle stesse autorizzazioni, pertanto non è necessario modificare le autorizzazioni.

   a) Nella scheda **[!UICONTROL Places Core Services]** , verifica quanto segue:

   * Nella parte inferiore della scheda vengono visualizzati due punti.
   * Il punto a sinistra è nero.

   b) Fare clic su **[!UICONTROL + Assegna utenti]**.

   c. Immetti l’Adobe ID dell’utente.

   d. Completa uno dei seguenti passaggi:

   * Se si aggiunge un nuovo utente, fare clic su **[!UICONTROL Nuovo utente]** e immettere il nome e il cognome dell&#39;utente.
   * Se aggiungi un utente esistente, fai clic sul nome dell’utente visualizzato.

   e. Nell&#39;elenco a discesa **[!UICONTROL Selezionare un profilo per questo prodotto]**, selezionare il profilo Luoghi.

   f. Fai clic su **[!UICONTROL Salva]**.

### Aggiungi uno sviluppatore

Per gli utenti che necessitano anche dell’accesso all’API dei servizi web, è necessario aggiungerli come sviluppatore.

Per aggiungere uno sviluppatore:

1. Nella scheda **[!UICONTROL Places Core Services]**, verifica quanto segue:

   * Nella parte inferiore della scheda vengono visualizzati due punti.
   * Fai clic sul punto a destra in modo che **[!UICONTROL Assegna sviluppatori]** venga visualizzato nella parte inferiore della scheda.

1. Fai clic su **[!UICONTROL + Assegna sviluppatori]**.

1. Inserisci l’Adobe ID dell’utente.

1. Completa uno dei seguenti passaggi:

   * Se stai aggiungendo un nuovo utente, fai clic su **[!UICONTROL Nuovo utente]** e immetti il nome e il cognome dell’utente.
   * Se aggiungi un utente esistente, fai clic sul nome dell’utente visualizzato.

1. Nell&#39;elenco a discesa **[!UICONTROL Selezionare un profilo per questo prodotto]**, selezionare il profilo Servizio Luoghi.

1. Fai clic su **[!UICONTROL Salva]**.

Gli utenti ricevono un messaggio e-mail con la conferma di accesso a Experience Platform Launch. Possono accedere all&#39;interfaccia utente [Experience Platform Launch](https://launch.adobe.com) o [Places Service](https://places.adobe.com) di questa organizzazione. Se completi il passaggio 4 della procedura **[!UICONTROL Aggiungi gli sviluppatori]**, l’utente può accedere anche alla [console Adobe I/O](https://console.adobe.io) per creare un’integrazione di Luoghi e utilizzare l’API REST Luoghi.
