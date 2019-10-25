---
title: Domande frequenti
seo-title: Domande frequenti
description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
seo-description: Questo argomento fornisce ulteriori informazioni su alcune domande frequenti.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Domande frequenti

Seguono alcune informazioni e domande frequenti su Location Service.

## Dimensioni e affidabilità

Importante da notare che tutte le aree geografiche utilizzate nel monitoraggio regionale da un'app mobile indipendentemente dall'utilizzo di Adobe o di altri servizi. I sistemi operativi consigliano alcuni parametri da tenere a mente durante la creazione di aree geografiche. Per la massima affidabilità, le aree geografiche devono avere un raggio di almeno 100 metri. È possibile creare aree geografiche più piccole, ma gli eventi di entrata e uscita potrebbero non essere generati o potrebbero essere generati dopo che l'utente ha smesso di muoversi per un periodo.

Inoltre, la precisione e l'affidabilità possono essere ridotte in base a condizioni hardware come lo spegnimento o la mancata disponibilità del wi-fi, e anche in base alla posizione del dispositivo in relazione all'impedimento dei segnali GPS. Ad esempio, le aree montane, le impostazioni urbane e le aree interne possono ridurre la precisione della posizione dai sistemi operativi iOS e Android.

## In che modo viene attivato un evento exit?

Quando l’SDK (Places Monitor) riceve un nuovo elenco di POI vicini, registra una regione con il sistema operativo per ciascun POI. Il sistema operativo ora è responsabile della notifica dell’SDK quando il dispositivo attraversa un limite (entrata o uscita) per una delle aree monitorate. L'SDK attiva un evento exit solo quando il sistema operativo notifica all'SDK che l'evento si è verificato. Il motivo principale di questa notifica è la sensibilità temporale dei dati sulla posizione.

Se il sistema operativo non è in grado di fornire un evento exit quando il dispositivo lascia un'area, è più sicuro che l'SDK ometta semplicemente l'evento exit. Se l’SDK produce un evento exit senza che l’evento venga attivato dal sistema operativo, esiste il rischio che l’evento exit venga elaborato correttamente al di fuori del periodo di tempo durante il quale il dispositivo si trovava vicino al POI.

## Aggiunta di un utente a Location Service e Experience Platform Launch {#adding-user-launch-places}

Per consentire agli utenti di accedere all’interfaccia utente [di](https://places.adobe.com)Launch Service, è necessario aggiungerli a Places Core Service nell’Admin Console come utente. Per consentire agli utenti di accedere a Experience Platform Launch, configurare le proprietà dei dispositivi mobili e utilizzare Places con l’SDK di Adobe Experience Platform, è necessario aggiungerli ad Experience Platform Launch nell’Admin Console e ottenere le seguenti autorizzazioni per Experience Platform Launch:

* Tutti i diritti di proprietà:
   * Develop
   * Approva
   * Pubblica
   * Gestire le estensioni
   * Gestione degli ambienti
* Autorizzazione Gestisci proprietà in Diritti aziendali

Se è la prima volta che aggiungete un utente, completate i seguenti passaggi per aggiungere utenti a Experience Platform Launch and Location Service. Se avete già aggiunto degli utenti, potrebbero essere visualizzati più profili, in modo da assicurarvi di selezionare il profilo corretto.

>[!IMPORTANT]
>
>Solo gli amministratori dell'organizzazione possono accedere ad Admin Console e aggiungere gli utenti.

### 1. Verifica il provisioning di Location Service e Experience Platform Launch

Per verificare che sia stato eseguito il provisioning di Location Service e Experience Platform Launch:

1. Accedi alla tua organizzazione Experience Cloud.
1. In alto a destra, fai clic sul commutatore di shell Experience Cloud.

   ![commutatore shell](/help/assets/places_shell_switcher1.png)

1. Alla voce **[!UICONTROL Platform]**, fai clic su **[!UICONTROL Administration]**.

   Se nell’elenco non è presente **Amministrazione** , non si è un amministratore. Per completare questa procedura, è necessario contattare l’amministratore dell’organizzazione.

1. Nella pagina Amministrazione di Experience Cloud, sulla **[!UICONTROL Admin Console]** scheda, fai clic su **[!UICONTROL Take me there]**.

1. In Admin Console, se hai accesso a diverse organizzazioni, verifica che l’organizzazione corretta sia selezionata in alto a destra nella pagina.

   Questa è l'organizzazione a cui aggiungerete i vostri utenti. Se l’organizzazione corretta non è stata selezionata, fate clic sull’organizzazione e selezionate l’organizzazione dall’elenco a discesa.

   >[!IMPORTANT]
   >
   >Se non avete accesso a un'organizzazione, significa che non disponete dell'accesso dell'amministratore a tale organizzazione.

1. Verificate che le schede per **[!UICONTROL Adobe Experience Platform Launch]** e **[!UICONTROL Places Core Services]** siano visualizzate.

   ![](/help/assets/places_provisioned1.png)

   Se visualizzati, sono stati forniti i servizi di localizzazione e il lancio della piattaforma Experience. Se non vengono visualizzati, è necessario fornire il provisioning per l'organizzazione.

   >[!IMPORTANT]
   >
   >Durante il periodo Beta, dopo aver completato il sondaggio [](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)Beta, la richiesta viene fatta al team Provisioning.

### 2. Configurare il profilo e aggiungere le autorizzazioni

Per impostare il profilo e aggiungere le autorizzazioni:

1. Configurate un profilo Experience Platform Launch che consente agli utenti aggiunti al profilo di utilizzare Experience Platform Launch e le relative proprietà mobili con l’SDK di Experience Platform.

   a. Nella barra dei menu, fate clic su **[!UICONTROL Product]**.

   b. Nel riquadro a sinistra, nell’elenco dei prodotti, fate clic su **[!UICONTROL Adobe Experience Platform Launch]**.

   * I profili di Launch della piattaforma Experience appaiono a destra.
   * Experience Platform Launch ha un profilo predefinito chiamato *Launch - (nome organizzazione)* .

      Se in precedenza hai aggiunto utenti a Experience Platform Launch, potrebbero essere elencati più profili.

2. Seleziona il profilo corretto:

   a. Fare clic sul nome del profilo predefinito.

   b.Fate clic sulla **[!UICONTROL Permissions]** scheda.

   c. Fate clic su **[!UICONTROL Edit]** accanto a **[!UICONTROL Property Rights]**.

   d. Nel riquadro a sinistra, fare clic su **[!UICONTROL + Add all]**.

   Questo passaggio sposta tutte le autorizzazioni disponibili nell'elenco delle autorizzazioni incluse.

   e.Fate clic **[!UICONTROL Company Rights]**.

   f. Nel riquadro a sinistra, fare clic su **[!UICONTROL + Manage Properties]**.

   g.Fate clic **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Per il servizio di localizzazione è presente un profilo predefinito, ma non è necessario aggiungere alcuna autorizzazione.

Sono state aggiunte le autorizzazioni al profilo creato.

### 3. Aggiungi un utente o uno sviluppatore ai profili di avvio del servizio di localizzazione e della piattaforma esperienza

Puoi aggiungere un utente e/o uno sviluppatore ai profili Location Service e Experience Platform Launch.

### Aggiungere un utente

Per aggiungere un utente ai profili di avvio di Location Service e Experience Platform:

1. Aggiungi un utente al profilo Experience Platform Launch.

   a. Nella barra dei menu, fate clic su **[!UICONTROL Overview]**.

   b.Nella **[!UICONTROL Adobe Experience Platform Launch]** scheda, verificate quanto segue:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Il punto a sinistra è nero.

      Se il punto a destra è nero, potete aggiungere solo sviluppatori. Per aggiungere un utente, fate clic sul punto a sinistra.
   c.Fate clic **[!UICONTROL + Add Users]**.

   d. Immettete l’Adobe ID dell’utente.

   e. Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic **[!UICONTROL New user]** e immettete il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.
   f. Nell’elenco a **[!UICONTROL Please select a profile for this product]** discesa, selezionate il profilo modificato in precedenza.

   g.Fate clic **[!UICONTROL Save]**.

2. Aggiungete un utente a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Attualmente, tutti gli utenti del servizio di localizzazione dispongono delle stesse autorizzazioni, pertanto non è necessario modificare le autorizzazioni.

   a.Nella **[!UICONTROL Places Core Services]** scheda, verificate quanto segue:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Il punto a sinistra è nero.
   b.Fate clic **[!UICONTROL + Assign Users]**.

   c. Immettete l’Adobe ID dell’utente.

   d. Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic **[!UICONTROL New user]** e immettete il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.
   e. Nell'elenco a **[!UICONTROL Please select a profile for this product]** discesa, selezionare il profilo Luoghi.

   f.Fate clic **[!UICONTROL Save]**.

### Aggiunta di uno sviluppatore

Per gli utenti che necessitano anche dell'accesso a Web Service API, è necessario aggiungerli come sviluppatore.

Per aggiungere uno sviluppatore:

1. Nella **[!UICONTROL Places Core Services]** scheda, verificate quanto segue:

   * Due punti vengono visualizzati nella parte inferiore della scheda.
   * Fate clic sul punto a destra in modo che **[!UICONTROL Assign Developers]** venga visualizzato nella parte inferiore della scheda.

1. Fai clic su **[!UICONTROL + Assign Developers]**.

1.  Immettete l’Adobe ID dell’utente.

1.  Completa uno dei seguenti passaggi:

   * Se state aggiungendo un nuovo utente, fate clic su di esso **[!UICONTROL New user]** e inserite il nome e il cognome dell’utente.
   * Se state aggiungendo un utente esistente, fate clic sul nome dell’utente visualizzato.

1. Nell'elenco a **[!UICONTROL Please select a profile for this product]** discesa, selezionate il profilo Location Service.

1. Fai clic su **Salva**.

Gli utenti ricevono un messaggio e-mail con la notifica di avere accesso a Experience Platform Launch. Possono accedere al lancio [della piattaforma](https://launch.adobe.com) Experience [o all’interfaccia utente](https://places.adobe.com) Luoghidi questa organizzazione. Se completi il passaggio 4 della procedura **Aggiungi uno sviluppatore** , l’utente può accedere anche alla console [I/O di](https://console.adobe.io) Adobe per creare un’integrazione Luoghi e utilizzare l’API REST Luoghi.