---
title: Notifiche push
description: In questa sezione viene illustrato come utilizzare il servizio Luoghi con le notifiche push.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 8%

---


# Notifiche push

Mobile Services consente di inviare notifiche push  segmenti Adobe Analytics. In Places Service, puoi segmentare il pubblico per il messaggio push utilizzando le loro interazioni storiche con i tuoi POI. Ad esempio, puoi inviare un messaggio agli utenti che si sono trovati in uno dei tuoi negozi negli ultimi 30 giorni.

Prima di iniziare, accertarsi di aver completato le seguenti attività:

* I dati del servizio Luoghi sono stati elaborati da  Adobe Analytics.

   Ciò significa che l&#39;app mobile ha inviato correttamente i dati del servizio Luoghi in una suite di rapporti e che i dati sono disponibili per la segmentazione.

* Il canale di notifica push in Mobile Services è configurato.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Informazioni su come inviare una notifica push a un segmento di Analytics in Mobile Services.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Invio di una notifica

Nella **[!UICONTROL Audience]** scheda del flusso di lavoro *Crea notifica* push, puoi creare il pubblico per questo messaggio in uno dei modi seguenti:

* Nell&#39;elenco a **[!UICONTROL Analytics Segments]** discesa, seleziona un segmento Adobe Analytics creato in precedenza.

* Nella **[!UICONTROL Custom Segment]** sezione, crea un&#39;audience utilizzando i parametri di segmento personalizzati disponibili.

![impostazione di un messaggio push](/help/assets/push-set-up.png)
