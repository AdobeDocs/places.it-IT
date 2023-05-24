---
title: Rapporto sui dati relativi alla posizione in Analytics Workspace
description: Questa sezione fornisce informazioni su come creare rapporti sui dati relativi alla posizione in Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# Rapporto sui dati relativi alla posizione nell’area di lavoro di Analytics {#places-in-workspace}

Questo documento mostra un esempio di come creare rapporti sui dati della posizione nell’area di lavoro di Analytics. Ogni passaggio conterrà un riepilogo di alto livello, con i dettagli forniti facendo riferimento ad altre pagine della documentazione.

## Prerequisiti

Il presente documento presuppone quanto segue:

1. L’estensione Luoghi viene implementata nell’applicazione.

   Per ulteriori informazioni sull’implementazione dell’estensione Luoghi, consulta [Estensioni Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. L’utente Adobe Analytics è un amministratore e ha accesso alle regole di elaborazione.

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Nella proprietà Launch, sono stati creati elementi dati per le variabili Places Service desiderate.

   Per ulteriori informazioni sugli elementi dati in Launch, consulta [Definire un elemento dati](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Creare una regola Launch

Crea una regola in base alla quale l’SDK invierà i dati ad Analytics quando il dispositivo entrerà in un POI. La creazione di questo tipo di regola è descritta nel [Inviare dati di entrata e uscita POI ad Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) pagina.

In questo esempio, per l’azione della regola sono definiti i seguenti valori per la richiesta Analytics:

* **[!UICONTROL Azione]** viene fornito un valore di **[!UICONTROL Voce Places]**.

* Chiave dati contestuali **[!UICONTROL poi.name]** è impostato sul valore dell’elemento dati **[!UICONTROL {%%POI Name%%}]**.

![&quot;imposta un&#39;azione&quot;](/help/assets/pt-setAction.png)

## 2. Creare le variabili di Analytics

Per mappare i dati contestuali (inviati nel passaggio 1), è necessario creare prima le variabili per la suite di rapporti di Analytics. Per ulteriori informazioni sulla creazione di variabili in Analytics, consulta [Variabili di conversione (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

In questo esempio, una variabile di conversione, **[!UICONTROL Evar2]**, è stato creato e denominato **[!UICONTROL Nome POI Places]**. Dovranno essere create ulteriori variabili per ogni variabile di posizione che desideri esporre nel reporting.

![&quot;creare una variabile di analisi&quot;](/help/assets/aa-evar.png)

## 3. Creare regole di elaborazione

Questo passaggio è necessario per mappare i dati contestuali (passaggio 1) alle variabili di Analytics (passaggio 2). Per ulteriori informazioni sulla creazione di regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

In questo esempio, è stata creata una regola di elaborazione per mappare il valore dei dati contestuali **[!UICONTROL poi.name]** in **[!UICONTROL Nome POI Places (eVar 2)]**. Sarà necessario creare regole di elaborazione aggiuntive per ogni variabile di posizione creata.

![&quot;creare una regola di elaborazione&quot;](/help/assets/aa-processing-rule.png)

## 4. Generare un rapporto in Workspace

Questo passaggio mostra un rapporto di base in Analytics Workspace per visualizzare i dati raccolti nei passaggi 1-3. Per ulteriori informazioni sull’utilizzo di Analytics Workspace, consulta [Panoramica di Analytics Workspace](https://docs.adobe.com/content/help/it-IT/analytics/analyze/analysis-workspace/home.translate.html).

In questo esempio, il rapporto presenta le seguenti impostazioni:

* Metrica - **[!UICONTROL Occorrenze]**

* DIMENSION - **[!UICONTROL Nome azione]**

   * Suddiviso per Dimension - **[!UICONTROL Nome POI Places]**

![&quot;creare un rapporto in workspace&quot;](/help/assets/aa-workspace.png)
