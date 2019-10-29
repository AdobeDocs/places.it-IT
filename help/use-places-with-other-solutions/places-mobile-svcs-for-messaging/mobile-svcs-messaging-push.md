---
title: Messaggi push
seo-title: Messaggi push
description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi push.
seo-description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi push.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Notifiche push (#place-push-messaging)

Notifica push: AMS consente di inviare notifiche push ai segmenti di Adobe Analytics. Il servizio Location consente di segmentare il pubblico del messaggio push in base alle interazioni storiche con i POI. Ad esempio, puoi inviare un messaggio agli utenti che si sono trovati in uno dei tuoi negozi negli ultimi 30 giorni.

Prima di iniziare, accertarsi di aver completato le seguenti attività:

* I dati del servizio di localizzazione sono stati elaborati da Adobe Analytics.

   Ciò significa che l'app mobile ha inviato correttamente i dati del servizio di localizzazione in una suite di rapporti e che i dati sono disponibili per la segmentazione.

* Il canale di notifica push in Mobile Services è configurato.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Scopri come inviare una notifica push a un segmento Analytics in Mobile Services.

   * Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Invio di una notifica

Nella **[!UICONTROL Audience]** scheda del flusso di lavoro *Crea notifica* push, puoi creare il pubblico per questo messaggio in uno dei modi seguenti:

* Seleziona un segmento di Adobe Analytics creato in precedenza.

* Crea un'audience utilizzando i parametri di segmento personalizzati disponibili.

![impostazione di un messaggio push](/help/assets/push-set-up.png)

