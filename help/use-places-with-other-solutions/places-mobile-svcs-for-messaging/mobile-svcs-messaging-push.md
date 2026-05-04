---
title: Notifiche push
description: Questa sezione illustra come utilizzare Places Service con le notifiche push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

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
