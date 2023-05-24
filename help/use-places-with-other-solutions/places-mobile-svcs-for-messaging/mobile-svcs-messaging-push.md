---
title: Notifiche push
description: Questa sezione illustra come utilizzare Places Service con le notifiche push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 8%

---

# Notifiche push

Mobile Services consente di inviare notifiche push ai segmenti Adobe Analytics. In Places Service, puoi segmentare il pubblico per il messaggio push utilizzando le interazioni storiche con i punti di interesse. Ad esempio, puoi inviare un messaggio agli utenti che hanno visitato uno dei tuoi negozi negli ultimi 30 giorni.

Prima di iniziare, assicurati di aver completato le seguenti attività:

* I dati di Places Service sono stati elaborati da Adobe Analytics.

   Ciò significa che la tua app mobile ha inviato correttamente i dati di Places Service in una suite di rapporti e che i dati sono disponibili per la segmentazione.

* Il canale di notifica push in Mobile Services è configurato.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Scopri come inviare una notifica push a un segmento Analytics in Mobile Services.

   Per ulteriori informazioni, consulta [Creare un messaggio push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Inviare una notifica

Il giorno **[!UICONTROL Pubblico]** scheda di *Creare una notifica push* flusso di lavoro, puoi creare il pubblico per questo messaggio in uno dei seguenti modi:

* In **[!UICONTROL Segmenti di Analytics]** , seleziona un segmento di Adobe Analytics creato in precedenza.

* In **[!UICONTROL Segmento personalizzato]** sezione, crea un pubblico utilizzando i parametri di segmenti personalizzati disponibili.

![configurazione di un messaggio push](/help/assets/push-set-up.png)
