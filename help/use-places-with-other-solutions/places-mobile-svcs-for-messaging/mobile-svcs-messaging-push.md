---
title: Notifiche push
seo-title: Notifiche push
description: In questa sezione viene illustrato come utilizzare Luoghi con le notifiche push.
seo-description: In questa sezione viene illustrato come utilizzare Luoghi con le notifiche push.
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# Notifiche push (#place-push-messaging)

Mobile Services consente di inviare notifiche push ai segmenti di Adobe Analytics. In Location Service, puoi segmentare il pubblico per il messaggio push utilizzando le loro interazioni storiche con i tuoi POI. Ad esempio, puoi inviare un messaggio agli utenti che si sono trovati in uno dei tuoi negozi negli ultimi 30 giorni.

Prima di iniziare, accertarsi di aver completato le seguenti attività:

* I dati del servizio di localizzazione sono stati elaborati da Adobe Analytics.

   Ciò significa che l’app mobile ha inviato correttamente i dati Location Service in una suite di rapporti e che i dati sono disponibili per la segmentazione.

* Il canale di notifica push in Mobile Services è configurato.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Informazioni su come inviare una notifica push a un segmento di Analytics in Mobile Services.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Invio di una notifica

Nella **[!UICONTROL Audience]** scheda del flusso di lavoro *Crea notifica* push, puoi creare il pubblico per questo messaggio in uno dei modi seguenti:

* Nell'elenco a **[!UICONTROL Analytics Segments]** discesa, seleziona un segmento di Adobe Analytics creato in precedenza.

* Nella **[!UICONTROL Custom Segment]** sezione, crea un'audience utilizzando i parametri di segmento personalizzati disponibili.

![impostazione di un messaggio push](/help/assets/push-set-up.png)