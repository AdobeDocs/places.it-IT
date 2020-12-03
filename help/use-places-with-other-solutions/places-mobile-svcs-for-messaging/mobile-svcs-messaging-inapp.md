---
title: Notifiche in-app
description: In questa sezione viene illustrato come utilizzare il servizio Luoghi con i messaggi in-app.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 5%

---


# Notifiche in-app {#places-push-messaging}

Le informazioni seguenti mostrano come configurare i messaggi in-app per l&#39;attivazione dagli eventi del servizio Luoghi.

>[!IMPORTANT]
>
>I messaggi devono trovarsi in un hit Analytics.

## Messaggio in-app

Mobile Services consente di utilizzare i dati della posizione che vengono inviati ad Analytics come evento o condizione di attivazione per un messaggio in-app. Se i messaggi in-app vengono attivati dall&#39;SDK e non è necessario attendere che i dati vengano elaborati da Analytics, i messaggi possono essere visualizzati in tempo reale non appena si verifica l&#39;attivazione.

### Notifiche locali

Elenco dei tipi di messaggi in-app disponibili:

* A schermo intero
* Avviso
* Notifiche locali

Questi tipi sono messaggi in-app perché sono attivati dall&#39;SDK. Le notifiche locali appaiono come notifiche push perché vengono visualizzate quando l&#39;app è in background. Queste notifiche forniscono anche notifiche in tempo reale quando gli utenti immettono o chiudono i POI mentre l’app è in background. Per ulteriori informazioni, consultate Estensione [Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)posizioni.

### Prerequisiti  

Prima di iniziare, scopri come inviare e creare un messaggio in-app in Mobile Services e come funzionano i trigger. Per ulteriori informazioni, consulta [Creare un messaggio in-app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regole in Experience Platform Launch

Puoi creare regole di Experience Platform Launch che inviano ad Analytics i dati che desideri usare come parte delle regole di attivazione messaggi in-app. È possibile utilizzare i dati delle estensioni Luoghi nelle regole del Experience Platform Launch come eventi e/o condizioni a seconda del caso d&#39;uso.

* Utilizzo dei dati sulla posizione come evento di attivazione.

   Ad esempio, puoi inviare dati ad Analytics quando un utente inserisce un POI.

* Utilizzo dei dati della posizione come condizione per un evento di attivazione.

   Ad esempio, se avete creato un tag di metadati personalizzato nel servizio Luoghi per il tempo in diversi POI, potete utilizzare tali metadati come parametro per la condizione Regola. Anche se potete utilizzare questa condizione con un evento POI descritto in precedenza, potete anche utilizzare la condizione come contesto per qualsiasi evento.

Una volta impostata la regola con i parametri di evento e condizione corretti, completa la configurazione della regola configurando l&#39;azione per l&#39;invio di dati ad Analytics.

## Crea un&#39;azione

Per creare un&#39;azione:

1. Seleziona l&#39;estensione **[!UICONTROL Adobe Analytics]**.
1. Nell&#39;elenco a **[!UICONTROL Action type]** discesa, seleziona **[!UICONTROL Track.]**
1. Digitare un nome per l&#39;azione.
1. Nel riquadro a destra, in **[!UICONTROL Context Data]**, selezionate la coppia chiave-valore per impostare i dati contestuali che verranno inviati ad Analytics.

Ad esempio, potete selezionare `poiname` come chiave e `{%%Last Entered POI Name}` come valore.

>[!TIP]
>
>È possibile impostare le regole di elaborazione di Analytics per recuperare i dati contestuali. Per ulteriori informazioni, consulta [Regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). Nell’esempio in *Creazione di un’azione*, l’azione invierà l’evento `poiname` come contesto per descrivere l’evento POI inviato ad Analytics.

![creazione di un&#39;azione](/help/assets/configure-action.png)

Esempio della regola completa:

![regola completata](/help/assets/create-a-rule.png)

## Creazione di un messaggio in-app in Mobile Services

Come parte dei parametri Trigger, puoi creare il pubblico per il messaggio con i dati provenienti dal Servizio Luoghi in uno dei modi seguenti:

* Utilizzo di azioni specifiche per la posizione, ad esempio una voce o un&#39;uscita.
* Utilizzo di metadati POI inviati come dati contestuali per limitare la destinazione del pubblico.

   Questa opzione può essere utilizzata con un&#39;azione specifica per una posizione, ad esempio una voce, o può essere utilizzata come contesto per un altro evento, ad esempio un avvio o un clic di pulsante.

   Di seguito è riportato un esempio di come configurare un messaggio in-app per accogliere gli utenti che immettono un POI con **[!UICONTROL Adobe]** il nome:

   ![parametri di attivazione](/help/assets/trigger-parameters.png)

* I parametri nelle intestazioni Servizio Luoghi della pagina *Triggers e Caratteristiche* di Mobile Services non funzionano con i dati di Servizio Luoghi.

   Questi parametri sono solo per il database legacy di Places Service creato in Mobile Services.