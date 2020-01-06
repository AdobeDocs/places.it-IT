---
title: Messaggi in-app con Location Service
description: Questa sezione fornisce informazioni sull'utilizzo dei messaggi push in Campaign Standard con messaggi in-app in Campaign Standard.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Messaggistica in-app con il servizio di localizzazione {#in-app-messages-loc-service}

Queste informazioni sono utili per comprendere come utilizzare le informazioni del servizio di localizzazione Adobe Experience Platform per inviare messaggi in-app o notifiche locali.

## Prerequisiti 

Prima di iniziare, effettuate le seguenti operazioni:

* Accertati che sia configurata un’applicazione mobile con l’SDK di Adobe Experience Platform Mobile, inclusa l’estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integra l’SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile nell’app.
* Aggiungi l&#39;estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard alla configurazione dell&#39;app mobile.

* [Create un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI Luoghi.

* Installa e configura le estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places e [Places Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) nell’applicazione mobile.

## Invio di un messaggio in-app in base a una voce o un&#39;uscita di recinto geografico

1. Nell&#39;istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Create In-App message]**.
1. Per il tipo di messaggio, selezionare **[!UICONTROL Target all users of a Mobile application]**.
1. Fare clic **[!UICONTROL Next]**e digitare i dettagli generali.
1. Nel riquadro a sinistra, verifica di poter utilizzare diversi attivatori relativi a Location Services.

   * Potete scegliere di visualizzare il messaggio in-app se l’utente ha inserito un limite geografico per i POI.
   * Potete anche utilizzare i metadati definiti nell&#39;interfaccia utente di Location Services per filtrare l&#39;audience.
   Nell&#39;esempio seguente, puoi attivare un messaggio in-app che viene visualizzato solo agli utenti che entrano in una delle località di vacanza che partecipano a un programma di bevande gratuite e vuoi inviare loro un coupon al loro arrivo.

   ![&quot;Metadati Luoghi messaggio in-app&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]**to finish creating the In-app message for delivery.

   ![&quot;create a event&quot;](/help/assets/prepare-ACS.png)

   Per verificare la consegna dei messaggi in-app, avvia l’applicazione in Xcode o Android studio e utilizza il simulatore di posizione per selezionare un POI che soddisfi i criteri di messaggistica.

   ![&quot;buono da bere&quot;](/help/assets/drink-coupon-on-app.png)

L&#39;utilizzo di Location Services con Adobe Campaign Standard vi offre uno strumento efficace per segmentare e indirizzare i vostri messaggi agli utenti in base a entrate ed uscite specifiche. Questa integrazione consente di creare casi di utilizzo più personalizzati e contestuali.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)