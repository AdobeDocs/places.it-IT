---
title: Panoramica sull'integrazione di Adobe I/O
description: Informazioni sulla creazione di un'integrazione Adobe I/O.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# Panoramica dell&#39;integrazione e prerequisiti {#integration-prereqs}

Queste informazioni mostrano come creare un&#39;integrazione Adobe I/O e un&#39;integrazione con i servizi Luoghi.

## Prerequisiti per l’accesso degli utenti

Verifica con l&#39;amministratore di sistema della tua organizzazione che siano state completate le seguenti attività:

* Il servizio di base posizioni viene visualizzato nella console di amministrazione dell&#39;azienda.
* È stato aggiunto all&#39;organizzazione.
* È stato aggiunto come utente al servizio di base Luoghi della tua organizzazione.

   Per ulteriori informazioni, consulta *Aggiungere un utente o uno sviluppatore ai profili* di avvio del servizio Places e della piattaforma Experience in Accesso [facilitato al servizio](/help/places-gain-access.md)Places.

* È stato aggiunto come sviluppatore al servizio core Luoghi della propria organizzazione.

   Per ulteriori informazioni sull’aggiunta di sviluppatori, vedi *Aggiungere un utente o uno sviluppatore ai profili* di avvio di Places Service e Experience Platform in Accesso [facilitato al servizio](/help/places-gain-access.md)Places.

   Per ulteriori informazioni sul ruolo di sviluppatore, consultate [Gestire gli sviluppatori](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### Richieste REST API

Ogni richiesta all&#39;API REST di Servizio Luoghi richiede i seguenti elementi:

* Un ID organizzazione
* Una chiave API
* Token portatore

Un&#39;integrazione con Adobe I/O fornisce questi elementi e un modo per richiedere il token del portatore utilizzando un JSON Web Token (JWT).

* Per ulteriori informazioni sui JWT, vedere [Introduzione ai Token](https://jwt.io/introduction/)Web JSON.
* Per creare un&#39;integrazione per il servizio Luoghi, vedete la sezione *Creazione di un&#39;integrazione* per il servizio Luoghi di seguito.
* Per comprendere l&#39;integrazione delle chiavi API, la generazione di un JWT e di certificati di chiave pubblica, vedi Panoramica [sull&#39;autenticazione dell&#39;I/O di](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)Adobe.

>[!IMPORTANT]
>
>Se non è possibile accedere alla console di I/O di Adobe o se il servizio Luoghi non è un&#39;opzione nella pagina ** Crea integrazioni, consultare Requisiti ** dell&#39;organizzazione nella panoramica [API dei servizi](/help/web-service-api/places-web-services.md)Web.

## Creazione di un&#39;integrazione con il servizio Luoghi

Per creare un&#39;integrazione con Places Service, completa le seguenti attività:

### Generazione di una coppia di chiavi pubblica e privata

Per creare un&#39;integrazione di Places Service, è necessario disporre di una coppia di chiavi pubblica e privata. Queste coppie possono essere acquistate, oppure è possibile generare chiavi autofirmate.

Per generare le chiavi autofirmate:

1. In una finestra terminale, copiate e incollate ciascuna delle seguenti righe e premete **[!UICONTROL Enter]**dopo aver incollato ciascuna riga:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >È consigliabile assegnare un nome alle chiavi per un riferimento semplice e memorizzarle in una cartella. Se create più integrazioni, potete facilmente identificare e gestire quali chiavi appartengono a quale integrazione.

1. Digitate le informazioni richieste da OpenSSL:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Per ulteriori informazioni su OpenSSL, consultate [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >Le informazioni fornite vengono incorporate nelle chiavi.

1. Andate alla directory in cui si trovano i `.key` file e `.crt` i file.

   Ad esempio, in MacOS, passate a **[!UICONTROL Macintosh HD]**>**[!UICONTROL users]** > **[!UICONTROL (your user name)]**>**[!UICONTROL Keys]**.

Il seguente video illustra il processo di generazione della coppia di chiavi:

![video di integrazione](/help/assets/places_integration_video.gif)

### Creare un&#39;integrazione di Places Service nella console Adobe I/O

Per creare un&#39;integrazione con il servizio Luoghi:

1. Andate a [https://console.adobe.io](https://console.adobe.io) ed effettuate l&#39;accesso con il vostro Adobe ID.
1. Nella sezione **Avvio** rapido, fate clic su **Crea integrazione**.
1. Selezionate **[!UICONTROL Access an API]**e fate clic su**[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]**è il percorso predefinito.

1. Se hai accesso a più organizzazioni Experience Cloud, seleziona l’organizzazione dall’elenco a discesa in alto a destra.
1. Under **[!UICONTROL Experience Cloud]**, select**[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. Selezionate **[!UICONTROL New integration]**e fate clic su**[!UICONTROL Continue]**.
1. Nella schermata Crea una nuova integrazione, immettete un nome e una descrizione.
1. Trascinare il `xxxx_public.crt` file creato sopra nella zona di **[!UICONTROL Public keys certificates]**rilascio.
1. Selezionate un profilo di prodotto.

   Se non sai quale profilo selezionare, contatta l’amministratore di sistema.
1. At the bottom of the page, click **[!UICONTROL Create integration]**.
1. Dopo alcuni secondi, nella schermata *Integrazione creata* , verifica che venga visualizzato il messaggio seguente:

   `Your integration has been created.`

1. Viene visualizzata la pagina dei dettagli dell’integrazione con il nome dell’integrazione nella parte superiore.

   La **[!UICONTROL Overview]**scheda viene visualizzata per impostazione predefinita e contiene la chiave API, l&#39;ID organizzazione, l&#39;ID account tecnico e altri dettagli sulle integrazioni.

### Registrazione dell&#39;ID organizzazione e della chiave API

1. Nella pagina dei dettagli dell&#39;integrazione, fate clic sulla **[!UICONTROL Services]**scheda e confermate che**[!UICONTROL Places Service]** sia visualizzata in **[!UICONTROL Configured Services]**.
1. Nella **[!UICONTROL Overview]**scheda, individua e registra la chiave API (ID client) e l&#39;ID organizzazione.

   Questi ID sono necessari per ogni richiesta REST API di Servizio Places.

![](/help/assets/places_orgid_api-key.png)

### Generazione di un token JWT

Nella pagina dei dettagli dell&#39;integrazione, fate clic sulla **[!UICONTROL JWT]**scheda per verificare l&#39;integrazione generando un JWT e fornendo l&#39;URL di scambio.

Per generare un token JWT:

1. In un editor di testo, aprite il `private.key` file creato precedentemente.
1. On the **[!UICONTROL JWT]**tab, copy the contents of the key and paste it in the**[!UICONTROL Paste private key]** field.
1. Fai clic su **[!UICONTROL Generate JWT]**.
1. In the **[!UICONTROL Sample CURL command]**section, click**[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. Eseguire il comando premendo **[!UICONTROL Enter]**sulla tastiera.
1. Individuare il `"token_type": "bearer"` valore e il `"access_token"` valore.

   Il valore del token di accesso del portatore è il valore che verrà utilizzato nelle richieste API del servizio Places.

>[!IMPORTANT]
>
>I token di accesso Adobe sono validi **solo** per 24 ore, quindi salvate il comando CURL di esempio (passaggio 5). Se il token di accesso non è più valido, è necessario rigenerare il token.