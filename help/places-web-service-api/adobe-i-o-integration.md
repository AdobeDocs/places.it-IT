---
title: Panoramica sull'integrazione di Adobe I/O
seo-title: Panoramica sull'integrazione di Adobe I/O
description: Informazioni sulla creazione di un'integrazione Adobe I/O.
seo-description: Informazioni sulla creazione di un'integrazione Adobe I/O.
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Panoramica sull'integrazione di Adobe I/O {#adobeio-integration}

Ogni richiesta all'API REST di Places richiede i seguenti elementi:

* Un ID organizzazione
* Una chiave API
* Token portatore

Un'integrazione con Adobe I/O fornisce questi elementi e un modo per richiedere il token del portatore utilizzando un JSON Web Token (JWT).

## Informazioni aggiuntive

* Per ulteriori informazioni sui JWT, vedere [Introduzione ai Token](https://jwt.io/introduction/)Web JSON.
* Per creare un'integrazione per Luoghi, consultate la sezione *Creazione di un'integrazione* per Luoghi di seguito.
* Per comprendere l'integrazione delle chiavi API, la generazione di un JWT e di certificati di chiave pubblica, vedi Panoramica [sull'autenticazione dell'I/O di](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)Adobe.

>[!IMPORTANT]
>
>Se non riuscite ad accedere alla console Adobe I/O o se Experience Platform Location Service non è un'opzione disponibile nella pagina ** Crea integrazioni, consultate Requisiti *di* organizzazione nella panoramica [dei servizi Web](/help/places-web-service-api/places-web-services.md)Places.

## Creare un'integrazione Luoghi {#create-places-integration}

Per creare un'integrazione Luoghi, completa le seguenti attività:

### Generazione di una coppia di chiavi pubblica e privata

Per creare un'integrazione Luoghi, è necessario disporre di una coppia di chiavi pubblica e privata. Queste coppie possono essere acquistate, oppure è possibile generare chiavi autofirmate.

Per generare le chiavi autofirmate:

1. In una finestra terminale, copiate e incollate ciascuna delle seguenti righe e premete **[!UICONTROL Enter]** dopo aver incollato ciascuna riga:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >È consigliabile assegnare un nome alle chiavi per un riferimento semplice e memorizzarle in una cartella. Se create più integrazioni, potete facilmente identificare e gestire quali chiavi appartengono a quale integrazione.

2. Digitate le informazioni richieste da OpenSSL:

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

3. Andate alla directory in cui si trovano i `.key` file e `.crt` i file.

   Ad esempio, in iOS, andate a **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**.

Il seguente video illustra il processo di generazione della coppia di chiavi:

![](/help/assets/places_integration_video.gif)

### Creare un'integrazione Luoghi nella console Adobe I/O

Per creare un'integrazione Luoghi:

1. Andate a [https://console.adobe.io](https://console.adobe.io) ed effettuate l'accesso con il vostro Adobe ID.
2. Se hai accesso a più organizzazioni Experience Cloud, seleziona l’organizzazione dall’elenco a discesa a sinistra.
3. Fai clic su **[!UICONTROL New Integration]**.
4. Selezionate **[!UICONTROL Access an API]** e fate clic su **[!UICONTROL Continue]**.
5. In **[!UICONTROL Experience Cloud]**, selezionate **[!UICONTROL Places]** come servizio Adobe al quale desiderate integrare e fate clic su **[!UICONTROL Continue]**.
6. Selezionate **[!UICONTROL New integration]** e fate clic su **[!UICONTROL Continue]**.
7. Nella schermata *Crea nuova integrazione* , immettete un nome e una descrizione.
8. Trascinare il `xxxx_public.crt` file creato sopra nella zona di **[!UICONTROL Public keys certificates]** rilascio.
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. Dopo alcuni secondi, nella schermata *Integrazione creata* , verifica che venga visualizzato il messaggio seguente:

   `Your integration has been created.`

11. Fai clic su **[!UICONTROL Continue to integration details]**.

   Viene visualizzata una panoramica dell’integrazione con la chiave API, l’ID organizzazione, l’ID account tecnico e altri dettagli sulle integrazioni.

### Registrazione dell'ID organizzazione e della chiave API

1. Nella **[!UICONTROL Services]** scheda, verificare che **[!UICONTROL Places]** sia visualizzato.
2. Nella **[!UICONTROL Overview]** scheda, individua e registra la chiave API (ID client) e l'ID organizzazione.

   Questi ID sono necessari per ogni richiesta REST API di Places.

![](/help/assets/places_orgid_api-key.png)

### Generazione di un token JWT

Nella **[!UICONTROL JWT]** scheda, la console Adobe I/O consente di verificare l’integrazione generando un JWT e fornendo l’URL di scambio.

Per generare un token JWT:

1. In un editor di testo, aprite il `private.key` file creato precedentemente.
2. Nella **[!UICONTROL JWT]** scheda, copiare il contenuto della chiave e incollarlo nel **[!UICONTROL Paste private key]** campo.
3. Fai clic su **[!UICONTROL Generate JWT]**.
4. Nella **[!UICONTROL Sample CURL command]** sezione fare clic **[!UICONTROL Copy]** e incollare il contenuto nella finestra del prompt dei comandi o terminale.
5. Eseguire il comando premendo **[!UICONTROL Enter]** sulla tastiera.
6. Individuare il `"token_type": "bearer"` valore e il `"access_token"` valore.

   Il valore del token di accesso del portatore è il valore che verrà utilizzato nelle richieste API Places.

>[!IMPORTANT]
>
>I token di accesso Adobe sono validi **solo** per 24 ore, quindi salvate il comando CURL di esempio (passaggio 5). Se il token di accesso non è più valido, è necessario generare di nuovo il token.

