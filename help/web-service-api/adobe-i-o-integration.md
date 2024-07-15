---
title: Panoramica del progetto Adobe Developer
description: Informazioni sulla creazione di un progetto API Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Panoramica e prerequisiti dell’accesso all’API Places {#developer-prereqs}

Queste informazioni mostrano come creare un progetto in Adobe Developer Console e generare un token di accesso da utilizzare nelle richieste API di Places.

## Prerequisiti per l’accesso degli utenti

Verifica con l’amministratore di sistema della tua organizzazione che siano state completate le seguenti attività:

* Sei stato aggiunto all’organizzazione.
* Sei stato aggiunto a un profilo all’interno di Adobe Experience Platform.

  Per ulteriori informazioni, consulta *Aggiungere un utente o uno sviluppatore al servizio Places e ai profili di Experience Platform Launch* in [Accedere a Places Service](/help/places-gain-access.md).

### Richieste REST API

Ogni richiesta all’API REST di Places Service richiede i seguenti elementi:

* Un ID organizzazione
* Una chiave API (nota anche come ID client)
* Segreto client
* Un token Bearer

Un progetto con la [console Adobe Developer](https://developer.adobe.com/console) fornisce questi elementi.

* Per creare un progetto per l&#39;API del servizio Places, consulta la sezione *Creazione di un progetto del servizio Places* di seguito.

>[!IMPORTANT]
>
>Se non riesci ad accedere alla [console Adobe Developer](https://developer.adobe.com/console) o se Places Service non è un&#39;opzione disponibile nella *pagina Crea integrazioni*, consulta *Requisiti dell&#39;organizzazione* in [Panoramica API dei servizi Web](/help/web-service-api/places-web-services.md).

## Creazione di un progetto API Places Service

Per creare un progetto per l’API del servizio Places, completa quanto segue:

1. Accedi al [sito Web Adobe Developer](https://developer.adobe.com) con il tuo Adobe ID.
2. Fai clic su **[!UICONTROL Console]** nell&#39;angolo superiore destro della pagina.
3. Se sei assegnato a più di un’organizzazione di Adobi, seleziona l’organizzazione corretta dall’elenco a discesa nell’angolo in alto a destra della pagina.
4. Fare clic sul pulsante **[!UICONTROL Crea nuovo progetto]**.
5. Fai clic sul pulsante **[!UICONTROL Aggiungi API]** nella sezione Introduzione al nuovo progetto.
6. Per selezionare l’API Luoghi, scorri la pagina verso il basso fino alla scheda Luoghi e fai clic sulla casella di controllo nell’angolo superiore destro della scheda.
7. Fai clic sul pulsante **[!UICONTROL Avanti]**.
8. Seleziona l’opzione OAuth Server-to-Server (se disponibile).
9. Assegna un nome alle credenziali e fai clic su **[!UICONTROL Avanti]**.
10. Seleziona un profilo (qualsiasi dovrebbe funzionare se è presente più di un profilo).
11. Fare clic su **[!UICONTROL Salva e configura API]**.
12. Nel pannello a sinistra, fai clic sul collegamento **[!UICONTROL Server-to-Server OAuth]** in CREDENZIALI
13. In questa pagina sono disponibili le informazioni seguenti:
   * Un modo per generare un token di accesso da utilizzare nelle richieste API REST di Places Service.
   * Visualizza un comando curl per un esempio di come generare un token di accesso dal tuo codice.
   * Visualizzare l’ID client (noto anche come chiave API)
   * Visualizza il segreto client
   * Visualizza l&#39;ID organizzazione
   * Tutti questi elementi sono richiesti nelle richieste all’API REST di Places Service.
14. Per rinominare il progetto in modo più descrittivo, fai clic sul nome del progetto nel percorso in alto a sinistra nella finestra
15. Quindi fare clic sul pulsante **[!UICONTROL Modifica progetto]** in alto a destra della pagina.

>[!IMPORTANT]
>
>I token di accesso Adobe sono **only** validi per 24 ore. Salvare quindi il comando CURL di esempio (passaggio 5). Se il token di accesso non è più valido, è necessario rigenerarlo.
