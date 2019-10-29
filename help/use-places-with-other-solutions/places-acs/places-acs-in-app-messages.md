---
title: Messaggi in-app con Location Service
seo-title: Messaggi in-app con Location Service
description: Questa sezione fornisce informazioni sull'utilizzo dei messaggi push in Campaign Standard con messaggi in-app in Campaign Standard.
seo-description: 'Questa sezione fornisce informazioni sull''utilizzo dei messaggi push in Campaign Standard con i messaggi in-app in Campaign Standard. '
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Messaggistica in-app con il servizio di localizzazione {#in-app-messages-loc-service}

Queste informazioni sono utili per comprendere come utilizzare le informazioni del servizio di localizzazione Adobe Experience Platform per inviare messaggi in-app o notifiche locali.

>[!IMPORTANT]
>
>Prima di iniziare, effettuate le seguenti operazioni:
>
>* Accertati che sia configurata un’applicazione mobile con l’SDK di Adobe Experience Platform Mobile, inclusa l’estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Integra l’SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile nell’app.
>* Aggiungi l'estensione [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard alla configurazione dell'app mobile.
   >
   >
* [Create un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) nell’interfaccia di gestione POI Luoghi.
   >
   >
* Installa e configura le estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places e [Places Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) nell’applicazione mobile.


## Invio di un messaggio in-app in base a una voce o un'uscita di recinto geografico

1. Nell'istanza di Adobe Campaign Standard, fai clic su **[!UICONTROL Create In-App message]**.
2. Selezionare il tipo di messaggio **[!UICONTROL Target all users of a Mobile application]**.
3. Fare clic **[!UICONTROL Next]** e digitare i dettagli generali.
4. Nel riquadro a sinistra, verifica di poter utilizzare diversi attivatori relativi a Location Services.

   * Potete scegliere di visualizzare il messaggio in-app se l’utente ha inserito un limite geografico per i POI.
   * Potete anche utilizzare i metadati definiti nell'interfaccia utente di Location Services per filtrare l'audience.
   Nell'esempio riportato nell'immagine seguente, puoi attivare un messaggio in-app che viene visualizzato solo agli utenti che sono entrati in una delle località di vacanza che partecipano a un programma di bevande gratuite, per inviare agli utenti un coupon al loro arrivo.

   !["Metadati Luoghi messaggio in-app"](/help/assets/last-entered-vacation.png)

5. Fai clic su per **[!UICONTROL Next]** terminare la creazione del messaggio in-app da consegnare.

   !["create a event"](/help/assets/prepare-ACS.png)

   Per verificare la consegna dei messaggi in-app, avvia l’applicazione in Xcode o Android studio e utilizza il simulatore di posizione per selezionare un POI che soddisfi i criteri di messaggistica.

   !["buono da bere"](/help/assets/drink-coupon-on-app.png)


L'utilizzo di Location Services con Adobe Campaign Standard vi offre uno strumento efficace per segmentare e indirizzare i vostri messaggi agli utenti in base a entrate ed uscite specifiche. Questa semplice integrazione apre la porta a casi di utilizzo più personalizzati e contestuali.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)