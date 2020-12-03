---
title: Report sui dati sulla posizione in Analytics Workspace
description: Questa sezione fornisce informazioni su come creare rapporti sui dati sulla posizione in Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 9%

---


# Report sui dati sulla posizione nell&#39;area di lavoro di Analytics {#places-in-workspace}

Questo documento mostra un esempio di come creare rapporti sui dati della posizione nell’area di lavoro di Analytics. Ogni passaggio conterrà un riepilogo di alto livello, con i dettagli forniti facendo riferimento ad altre pagine della documentazione.

## Prerequisiti  

Questo documento prevede quanto segue:

1. L&#39;estensione Luoghi è implementata nell&#39;applicazione.

   Per ulteriori informazioni sull&#39;implementazione dell&#39;estensione Luoghi, vedere Estensioni [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Luoghi.

1. L&#39;utente Adobe Analytics  è un amministratore e ha accesso alle regole di elaborazione.

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Nella proprietà Launch sono stati creati elementi di dati per le variabili del servizio Places desiderate.

   Per ulteriori informazioni sugli elementi dati in Launch, vedere [Definire un elemento](/help/use-places-launch-workflow/define-data-elements.md)dati.


## 1. Creare una regola di avvio

Crea una regola che farà in modo che l’SDK invii dati ad Analytics quando il dispositivo entra in un POI. La creazione di questo tipo di regola è descritta nella pagina [Invia dati di entrata e uscita POI ad Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

In questo esempio, l&#39;azione della regola ha i seguenti valori definiti per la richiesta Analytics:

* **[!UICONTROL Action]** viene fornito un valore di **[!UICONTROL Places Entry]**.

* La chiave dati contestuali **[!UICONTROL poi.name]** è impostata sul valore dell&#39;elemento dati **[!UICONTROL {%%POI Name%%}]**.

![&quot;imposta un&#39;azione&quot;](/help/assets/pt-setAction.png)

## 2. Creare variabili Analytics

Per mappare i dati contestuali (inviati nel passaggio 1), le variabili devono prima essere create per la suite di rapporti di Analytics. Per ulteriori informazioni sulla creazione di variabili in Analytics, vedi Variabili di [conversione (eVar)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

In questo esempio, è stata creata una variabile di conversione **[!UICONTROL Evar2]** con nome **[!UICONTROL Places POI Name]**. Sarà necessario creare ulteriori variabili per ogni variabile di posizione che si desidera esporre nel reporting.

![&quot;create una variabile di analisi&quot;](/help/assets/aa-evar.png)

## 3. Creare regole di elaborazione

Questo passaggio è necessario per mappare i dati contestuali (passaggio 1) alle variabili di Analytics (passaggio 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

In questo esempio, è stata creata una regola di elaborazione per mappare il valore dei dati contestuali **[!UICONTROL poi.name]** in **[!UICONTROL Places POI Name (eVar2)]**. Saranno necessarie ulteriori regole di elaborazione per ogni variabile di posizione creata.

![&quot;create una regola di elaborazione&quot;](/help/assets/aa-processing-rule.png)

## 4. Generazione di un rapporto in Workspace

Questo passaggio mostra un rapporto di base in Analytics Workspace per visualizzare i dati raccolti nei passaggi da 1 a 3. Per ulteriori informazioni sull’utilizzo di Analytics Workspace, consulta Panoramica [di](https://docs.adobe.com/content/help/it-IT/analytics/analyze/analysis-workspace/home.translate.html)Analytics Workspace.

In questo esempio, il rapporto ha le seguenti impostazioni:

* Metrica - **[!UICONTROL Occurrences]**

* Dimensione - **[!UICONTROL Action Name]**

   * Ripartizione per Dimension - **[!UICONTROL Places POI Name]**

![&quot;create a report in workspace&quot;](/help/assets/aa-workspace.png)
