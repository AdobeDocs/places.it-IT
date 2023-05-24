---
title: Messaggi in-app con Places Service
description: Questa sezione fornisce informazioni sull’utilizzo dei messaggi push in Campaign Standard con i messaggi in-app in Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Messaggistica in-app con Places Service {#in-app-messages-loc-service}

Queste informazioni spiegano come utilizzare le informazioni di Places Service per inviare messaggi in-app o notifiche locali.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un’app mobile configurata con Adobe Experience Platform Mobile SDK, incluso [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrare [SDK di Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nell’app.
* Aggiungi il [Estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione dell’app mobile.

* [Creare un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI di Places Service.

* Installare e configurare [Estensione Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md) e una soluzione di monitoraggio regionale ([Documentazione di CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS, oppure [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) nell&#39;app mobile.

## Invio di un messaggio in-app basato su una voce di recinto geografico o su un’uscita

1. Nell’istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Creare un messaggio in-app]**.
1. Per il tipo di messaggio, seleziona **[!UICONTROL Eseguire il targeting per tutti gli utenti di un’applicazione mobile]**.
1. Clic **[!UICONTROL Successivo]** e digita i dettagli generali.
1. Nel riquadro a sinistra, verifica di poter utilizzare diversi trigger correlati a Places Services.

   * Puoi scegliere di visualizzare il messaggio in-app se l’utente ha inserito un recinto geografico POI.
   * Per filtrare il pubblico, puoi anche utilizzare i metadati definiti nell’interfaccia utente di Places Services.

   Nell’esempio seguente, puoi attivare un messaggio in-app che viene visualizzato solo agli utenti che accedono a una delle località di vacanza che partecipano a un programma di bevande gratuite e desideri inviare a tali utenti un coupon quando arrivano.

   ![&quot;Metadati di In-App Message Places&quot;](/help/assets/last-entered-vacation.png)

1. Fai clic su **[!UICONTROL Successivo]** per completare la creazione del messaggio in-app da consegnare.

   ![&quot;crea un evento&quot;](/help/assets/prepare-ACS.png)

   Per testare la consegna dei messaggi in-app, avvia l’applicazione in Xcode o Android Studio e utilizza il simulatore di posizione per selezionare un POI che soddisfi i criteri di messaggistica.

   ![&quot;coupon da bere&quot;](/help/assets/drink-coupon-on-app.png)

L’utilizzo di Places Services con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base a entrate e uscite dal recinto geografico. Questa integrazione ti consente di creare casi d’uso più personalizzati e contestuali.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service con messaggistica per campagne](https://www.youtube.com/watch?v=ikiTTQw9c-o)
