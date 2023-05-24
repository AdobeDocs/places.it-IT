---
title: Panoramica sull’integrazione di Adobe I/O
description: Informazioni sulla creazione di un’integrazione Adobe I/O.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---

# Panoramica sull’integrazione e prerequisiti {#integration-prereqs}

Queste informazioni mostrano come creare un Adobe I/O e un’integrazione del servizio Places.

## Prerequisiti per l’accesso degli utenti

Verifica con l’amministratore di sistema della tua organizzazione che siano state completate le seguenti attività:

* Places Core Service viene visualizzato nell’Admin Console della tua organizzazione.
* Sei stato aggiunto all’organizzazione.
* Sei stato aggiunto come utente al servizio core Places nella tua organizzazione.

   Per ulteriori informazioni, consulta *Aggiungere un utente o uno sviluppatore ai profili di Experience Platform Launch e al servizio Places* in [Accedere a Places Service](/help/places-gain-access.md).

* Sei stato aggiunto come Sviluppatore al servizio core Places nella tua organizzazione.

   Per ulteriori informazioni sull’aggiunta di sviluppatori, consulta *Aggiungere un utente o uno sviluppatore ai profili di Experience Platform Launch e al servizio Places* in [Accedere a Places Service](/help/places-gain-access.md).

   Per ulteriori informazioni sul ruolo sviluppatore, consulta [Gestire gli sviluppatori](https://helpx.adobe.com/it/enterprise/using/manage-developers.html).

### Richieste REST API

Ogni richiesta all’API REST di Places Service richiede i seguenti elementi:

* Un ID organizzazione
* Una chiave API
* Un token Bearer

Un’integrazione con Adobe I/O fornisce questi elementi e un modo per richiedere il token Bearer utilizzando un token web JSON (JWT).

* Per ulteriori informazioni sui JWT, consulta [Introduzione ai token web JSON](https://jwt.io/introduction/).
* Per creare un’integrazione per Places Service, consulta *Creazione di un’integrazione di Places Service* sezione successiva.
* Per comprendere l’integrazione della chiave API, la generazione di un JWT e i certificati a chiave pubblica, consulta [Panoramica dell’autenticazione di Adobe I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Se non riesci ad accedere alla console Adobe I/O o se Places Service non è un’opzione nella *Pagina Crea integrazioni*, vedi *Requisiti dell’organizzazione* in [Panoramica API dei servizi Web](/help/web-service-api/places-web-services.md).

## Creare un’integrazione con Places Service

Per creare un’integrazione Places Service, completa le seguenti attività:

### Generare una coppia di chiavi pubblica e privata

Per creare un’integrazione Places Service, è necessaria una coppia di chiavi pubblica e privata. È possibile acquistare queste coppie oppure generare chiavi autofirmate.

Per generare chiavi autofirmate:

1. In una finestra del terminale, copiare e incollare ciascuna delle seguenti righe e premere **[!UICONTROL Invio]** dopo aver incollato ogni riga:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >È consigliabile assegnare un nome alle chiavi per un riferimento semplice e memorizzarle in una cartella. Se crei più integrazioni, puoi facilmente identificare e gestire quali chiavi appartengono a quale integrazione.

1. Digitare le informazioni richieste da OpenSSL:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Per ulteriori informazioni su OpenSSL, consulta [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >Le informazioni fornite vengono incorporate nelle chiavi.

1. Passa alla directory in cui `.key` e `.crt` i file si trovano.

   Ad esempio, in MacOS, vai a **[!UICONTROL Macintosh HD]** > **[!UICONTROL utenti]** > **[!UICONTROL (nome utente)]** > **[!UICONTROL Chiavi]**.

Il video seguente ti guida attraverso il processo di generazione della coppia di chiavi:

![video sull’integrazione](/help/assets/places_integration_video.gif)

### Creare un’integrazione di Places Service nella console di Adobe I/O

Per creare un’integrazione di Places Service:

1. Vai a [https://console.adobe.io](https://console.adobe.io) e accedi con il tuo Adobe ID.
1. In **Guida rapida** , fare clic su **Creare l’integrazione**.
1. Seleziona **[!UICONTROL Accedere a un’API]** e fai clic su **[!UICONTROL Continua]**.

   **[!UICONTROL Accedere a un’API]** è la posizione predefinita.

1. Se hai accesso a più organizzazioni di Experienci Cloud, seleziona l’organizzazione dall’elenco a discesa in alto a destra.
1. Sotto **[!UICONTROL Experience Cloud]**, seleziona **[!UICONTROL Places Service]** come servizio Adobe in cui desideri essere integrato e fai clic su **[!UICONTROL Continua]**.
1. Seleziona **[!UICONTROL Nuova integrazione]** e fai clic su **[!UICONTROL Continua]**.
1. Nella schermata Create a new integration (Crea una nuova integrazione), immetti un nome e una descrizione.
1. Trascina il file `xxxx_public.crt` creato in precedenza, al file **[!UICONTROL Certificati a chiave pubblica]** zona di rilascio.
1. Seleziona un profilo di prodotto.

   Se non sai quale profilo selezionare, contatta l’amministratore di sistema.
1. Nella parte inferiore della pagina, fai clic su **[!UICONTROL Creare l’integrazione]**.
1. Dopo alcuni secondi, nel *Integrazione creata* , verificare che venga visualizzato il seguente messaggio:

   `Your integration has been created.`

1. Viene visualizzata la pagina dei dettagli dell’integrazione con il nome dell’integrazione in alto.

   Il **[!UICONTROL Panoramica]** viene visualizzata per impostazione predefinita e contiene la chiave API, l’ID organizzazione, l’ID account tecnico e altri dettagli sulle integrazioni.

### Registra l’ID organizzazione e la chiave API

1. Nella pagina dei dettagli dell’integrazione, fai clic su **[!UICONTROL Servizi]** e confermare che **[!UICONTROL Places Service]** viene visualizzato in **[!UICONTROL Servizi configurati]**.
1. Il giorno **[!UICONTROL Panoramica]** , individua e registra la chiave API (ID client) e l’ID organizzazione.

   Questi ID sono necessari per ogni richiesta API REST di Places Service.

![](/help/assets/places_orgid_api-key.png)

### Generare un token JWT

Nella pagina dei dettagli dell’integrazione, fai clic su **[!UICONTROL JWT]** in modo da poter testare l’integrazione generando un JWT e fornendo l’URL di Exchange.

Per generare un token JWT:

1. In un editor di testo, apri `private.key` file creato in precedenza.
1. Nella scheda **[!UICONTROL JWT]**, copia il contenuto della chiave e incollalo nel campo **[!UICONTROL Paste private key]** (Incolla chiave privata).
1. Clic **[!UICONTROL Genera JWT]**.
1. Nella sezione del **[!UICONTROL comando Sample CURL]**, fai clic su **[!UICONTROL Copia]** e incolla il contenuto nel prompt dei comandi o nella finestra del terminale.
1. Eseguire il comando premendo **[!UICONTROL Invio]** sulla tastiera.
1. Individua il `"token_type": "bearer"` e `"access_token"` valore.

   Il valore del token di accesso bearer è ciò che utilizzerai nelle richieste API di Places Service.

>[!IMPORTANT]
>
>I token di accesso Adobe sono validi **solo** per 24 ore, quindi salvate il comando CURL di esempio (passaggio 5). Se il token di accesso non è più valido, devi rigenerarlo.
