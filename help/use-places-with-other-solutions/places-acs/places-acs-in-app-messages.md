---
title: Messaggi in-app con Places Service
description: Questa sezione fornisce informazioni sull’utilizzo dei messaggi push in Campaign Standard con messaggi in-app in Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Messaggistica in-app con Places Service {#in-app-messages-loc-service}

Queste informazioni sono utili per comprendere come utilizzare le informazioni del servizio Places per inviare messaggi in-app o notifiche locali.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un’app mobile configurata con l’SDK di Adobe Experience Platform Mobile, tra cui [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrare le [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nell’app.
* Aggiungi il [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione dell’app mobile.

* [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI di Places Service.

* Installa e configura il [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md) e una soluzione di monitoraggio regionale ([Documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS, oppure [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) nell’app mobile.

## Invio di un messaggio in-app in base a una voce di recinto geografico o all’uscita

1. Nella tua istanza Adobe Campaign Standard, fai clic su **[!UICONTROL Creare un messaggio in-app]**.
1. Per il tipo di messaggio, seleziona **[!UICONTROL Eseguire il targeting di tutti gli utenti di un&#39;applicazione mobile]**.
1. Fai clic su **[!UICONTROL Successivo]** e digitare i dettagli generali.
1. Nel riquadro a sinistra, verifica di poter utilizzare diversi attivatori correlati a Places Services.

   * Puoi scegliere di visualizzare il messaggio in-app se l’utente ha inserito una recinzione geografica POI.
   * Puoi anche utilizzare i metadati definiti nell’interfaccia utente di Places Services per filtrare il pubblico.

   Nell’esempio seguente, puoi attivare un messaggio in-app che viene visualizzato solo agli utenti che entrano in uno dei resort per le vacanze che partecipano a un programma di bevande gratuite e vuoi inviare a tali utenti un coupon al loro arrivo.

   ![&quot;Metadati di Places del messaggio in-app&quot;](/help/assets/last-entered-vacation.png)

1. Fai clic sul pulsante **[!UICONTROL Successivo]** per terminare la creazione del messaggio in-app da consegnare.

   ![&quot;crea un evento&quot;](/help/assets/prepare-ACS.png)

   Per testare la consegna dei messaggi in-app, avvia l’applicazione in Xcode o Android studio e utilizza il simulatore di posizione per selezionare un POI che si adatti ai criteri di messaggistica.

   ![&quot;buono da bere&quot;](/help/assets/drink-coupon-on-app.png)

L’utilizzo di Places Services con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base alle entrate e alle uscite del recinto geografico. Questa integrazione ti consente di creare casi d’uso più personalizzati e contestuali.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Servizio di posizione Adobe Experience Platform con i messaggi di Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
