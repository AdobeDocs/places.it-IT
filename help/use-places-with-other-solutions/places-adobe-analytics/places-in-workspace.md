---
title: Rapporto sui dati relativi alla posizione in Analytics Workspace
description: Questa sezione fornisce informazioni su come creare rapporti sui dati relativi alla posizione in Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
TQID: https://experienceleague.adobe.com/Xym9Ko8czyd3wYWVo22sQoK6gk-VvftGVHfIDUys06E
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: c20d46e7-1c7d-476c-a50e-3961d4dce35fid: daec7ead-f475-492a-a3b3-02ae08565d6fid: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 6%

---

# Rapporto sui dati relativi alla posizione nel Workspace di Analytics {#places-in-workspace}

Questo documento mostra un esempio di come creare rapporti sui dati relativi alla posizione nel Workspace di Analytics. Ogni passaggio conterrà un riepilogo di alto livello, con i dettagli forniti facendo riferimento ad altre pagine della documentazione.

## Prerequisiti

Il presente documento presuppone quanto segue:

1. L’estensione Luoghi viene implementata nell’applicazione.

   Per ulteriori informazioni sull&#39;implementazione dell&#39;estensione Luoghi, vedere [Estensioni Luoghi](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. L’utente Adobe Analytics è un amministratore e ha accesso alle regole di elaborazione.

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

1. Nella proprietà Launch, sono stati creati elementi dati per le variabili Places Service desiderate.

   Per ulteriori informazioni sugli elementi dati in Launch, vedere [Definire un elemento dati](/help/use-places-launch-workflow/define-data-elements.md).


## &#x200B;1. Creare una regola Launch

Crea una regola in base alla quale SDK invierà dati ad Analytics quando il dispositivo entrerà in un POI. La creazione di questo tipo di regola è descritta nella pagina [Invia dati di ingresso e uscita POI ad Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

In questo esempio, per l’azione della regola sono definiti i seguenti valori per la richiesta Analytics:

* **[!UICONTROL Action]** ha un valore di **[!UICONTROL Places Entry]**.

* La chiave dei dati contestuali **[!UICONTROL poi.name]** è impostata sul valore dell&#39;elemento dati **[!UICONTROL {%%POI Name%}]**.

![&quot;ha impostato un&#39;azione&quot;](/help/assets/pt-setAction.png)

## &#x200B;2. Creare le variabili di Analytics

Per mappare i dati contestuali (inviati nel passaggio 1), è necessario creare prima le variabili per la suite di rapporti di Analytics. Per ulteriori informazioni sulla creazione di variabili in Analytics, vedi [Variabili di conversione (eVar)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=it).

In questo esempio, è stata creata una variabile di conversione, **[!UICONTROL Evar2]**, denominata **[!UICONTROL Places POI Name]**. Dovranno essere create ulteriori variabili per ogni variabile di posizione che desideri esporre nel reporting.

![&quot;creare una variabile di analisi&quot;](/help/assets/aa-evar.png)

## &#x200B;3. Creare regole di elaborazione

Questo passaggio è necessario per mappare i dati contestuali (passaggio 1) alle variabili di Analytics (passaggio 2). Per ulteriori informazioni sulla creazione di regole di elaborazione, vedere [Panoramica sulle regole di elaborazione](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

In questo esempio, è stata creata una regola di elaborazione per mappare il valore dei dati contestuali **[!UICONTROL poi.name]** in **[!UICONTROL Places POI Name (eVar2)]**. Sarà necessario creare regole di elaborazione aggiuntive per ogni variabile di posizione creata.

![&quot;creare una regola di elaborazione&quot;](/help/assets/aa-processing-rule.png)

## &#x200B;4. Generare un rapporto in Workspace

Questo passaggio mostra un rapporto di base in Analytics Workspace per visualizzare i dati raccolti nei passaggi 1-3. Per ulteriori informazioni sull&#39;utilizzo di Analytics Workspace, vedere [Analytics Workspace overview](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=it).

In questo esempio, il rapporto presenta le seguenti impostazioni:

* Metrica - **[!UICONTROL Occorrenze]**

* Dimension - **[!UICONTROL Nome azione]**

   * Suddiviso per Dimension - **[!UICONTROL Nome POI luoghi]**

![&quot;creare un report nell&#39;area di lavoro&quot;](/help/assets/aa-workspace.png)
