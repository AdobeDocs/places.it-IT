---
title: Messaggi in-app con Places Service
description: Questa sezione fornisce informazioni sull’utilizzo dei messaggi push in Campaign Standard con i messaggi in-app in Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Messaggistica in-app con Places Service {#in-app-messages-loc-service}

Queste informazioni spiegano come utilizzare le informazioni di Places Service per inviare messaggi in-app o notifiche locali.

## Prerequisiti

Prima di iniziare, completa le seguenti attività:

* Avere un&#39;app mobile configurata con l&#39;SDK di Adobe Experience Platform Mobile, inclusa l&#39;estensione [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integra [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) nella tua app.
* Aggiungi l&#39;[estensione Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) alla configurazione della tua app mobile.

* [Crea un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell&#39;interfaccia di gestione POI di Places Service.

* Installa e configura l&#39;estensione [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) e una soluzione di monitoraggio per area geografica ([Documentazione CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) per iOS o [Documentazione sulla posizione Android](https://developer.android.com/training/location/geofencing)) nella tua app mobile.

## Invio di un messaggio in-app basato su una voce di recinto geografico o su un’uscita

1. Nell&#39;istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Crea messaggio in-app]**.
1. Per il tipo di messaggio, seleziona **[!UICONTROL Esegui il targeting di tutti gli utenti di un&#39;applicazione mobile]**.
1. Fai clic su **[!UICONTROL Avanti]** e digita i dettagli generali.
1. Nel riquadro a sinistra, verifica di poter utilizzare diversi trigger correlati a Places Services.

   * Puoi scegliere di visualizzare il messaggio in-app se l’utente ha inserito un recinto geografico POI.
   * Per filtrare il pubblico, puoi anche utilizzare i metadati definiti nell’interfaccia utente di Places Services.

   Nell’esempio seguente, puoi attivare un messaggio in-app che viene visualizzato solo agli utenti che accedono a una delle località di vacanza che partecipano a un programma di bevande gratuite e desideri inviare a tali utenti un coupon quando arrivano.

   Metadati di ![&quot;In-App Message Places&quot;](/help/assets/last-entered-vacation.png)

1. Fai clic su **[!UICONTROL Avanti]** per completare la creazione del messaggio in-app da consegnare.

   ![&quot;crea un evento&quot;](/help/assets/prepare-ACS.png)

   Per testare la consegna dei messaggi in-app, avvia l’applicazione in Xcode o Android studio e utilizza il simulatore di posizione per selezionare un POI che soddisfi i criteri di messaggistica.

   ![&quot;buono da bere&quot;](/help/assets/drink-coupon-on-app.png)

L’utilizzo di Places Services con Adobe Campaign Standard offre uno strumento potente per segmentare e indirizzare i messaggi agli utenti in base a entrate e uscite dal recinto geografico. Questa integrazione ti consente di creare casi d’uso più personalizzati e contestuali.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Servizio di posizione Adobe Experience Platform con messaggi di campagna](https://www.youtube.com/watch?v=ikiTTQw9c-o)
