---
title: Notifiche push
description: Questa sezione illustra come utilizzare Places Service con le notifiche push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# Notifiche push

Mobile Services consente di inviare notifiche push ai segmenti Adobe Analytics. In Places Service, puoi segmentare il pubblico per il messaggio push utilizzando le interazioni storiche con i punti di interesse. Ad esempio, puoi inviare un messaggio agli utenti che hanno visitato uno dei tuoi negozi negli ultimi 30 giorni.

Prima di iniziare, assicurati di aver completato le seguenti attività:

* I dati di Places Service sono stati elaborati da Adobe Analytics.

  Ciò significa che la tua app mobile ha inviato correttamente i dati di Places Service in una suite di rapporti e che i dati sono disponibili per la segmentazione.

* Il canale di notifica push in Mobile Services è configurato.

  Per ulteriori informazioni, consulta [Creare un messaggio push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=it).

* Scopri come inviare una notifica push a un segmento Analytics in Mobile Services.

  Per ulteriori informazioni, consulta [Creare un messaggio push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=it).

## Inviare una notifica

Nella scheda **[!UICONTROL Pubblico]** del flusso di lavoro *Crea notifica push*, puoi creare il pubblico per questo messaggio in uno dei seguenti modi:

* Nell&#39;elenco a discesa **[!UICONTROL Segmenti di Analytics]**, seleziona un segmento di Adobe Analytics creato in precedenza.

* Nella sezione **[!UICONTROL Segmento personalizzato]**, crea un pubblico utilizzando i parametri di segmento personalizzati disponibili.

![configurazione di un messaggio push](/help/assets/push-set-up.png)
