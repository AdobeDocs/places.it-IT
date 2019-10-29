---
title: Notifiche in-app
seo-title: Notifiche in-app
description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi in-app.
seo-description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi in-app.
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Notifiche in-app (#place-push-messaging)

Le informazioni seguenti mostrano come configurare i messaggi in-app da attivare dagli eventi Luoghi.

>[!IMPORTANT]
>
>I messaggi devono trovarsi in un hit Analytics.

## Messaggio in-app

Mobile Services consente di utilizzare i dati della posizione che vengono inviati ad Analytics come evento o condizione di attivazione per un messaggio in-app. Se i messaggi in-app vengono attivati dall'SDK e non è necessario attendere che i dati vengano elaborati da Analytics, i messaggi possono essere visualizzati in tempo reale non appena si verifica l'attivazione.

### Notifiche locali

Elenco dei tipi di messaggi in-app disponibili:

* A schermo intero
* Avviso
* Notifiche locali

Questi tipi sono messaggi in-app perché sono attivati dall'SDK. Le notifiche locali appaiono come notifiche push perché vengono visualizzate quando l'app è in background. Queste notifiche forniscono anche notifiche in tempo reale quando gli utenti immettono o chiudono i POI mentre l’app è in background. Per ulteriori informazioni, consultate Estensione [Monitor luoghi.](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)

### Prerequisiti

Prima di iniziare, scopri come inviare e creare un messaggio in-app in Mobile Services e come funzionano i trigger. Per ulteriori informazioni, consulta [Creare un messaggio in-app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regole in Experience Platform Launch

Puoi creare regole di Launch che inviano ad Analytics i dati che desideri usare come parte delle regole di attivazione messaggi in-app. Puoi utilizzare i dati delle estensioni Luoghi nelle regole di Launch come eventi e/o condizioni a seconda del caso d’uso.

* Utilizzo dei dati sulla posizione come evento di attivazione.

   Ad esempio, puoi inviare dati ad Analytics quando un utente inserisce un POI.

* Utilizzo dei dati della posizione come condizione per un evento di attivazione.

   Ad esempio, se avete creato un tag di metadati personalizzato nel servizio Posizione per il tempo in diversi POI, potete utilizzare tali metadati come parametro per la condizione Regola. Anche se potete utilizzare questa condizione con un evento POI descritto in precedenza, potete anche utilizzare la condizione come contesto per qualsiasi evento.

Una volta impostata la regola con i parametri di evento e condizione corretti, completa la configurazione della regola configurando l'azione per l'invio di dati ad Analytics.

## Crea un'azione

Per eseguire questa operazione:

1. Seleziona l'estensione **.[!UICONTROL Adobe Analytics]**
1. Nell'elenco a **[!UICONTROL Action type]** discesa, seleziona **[!UICONTROL Track.]**
1. Digitare un nome per l'azione.
1. Nel riquadro a destra, in **[!UICONTROL Context Data]**, selezionate la coppia chiave/valore per impostare i dati contestuali che verranno inviati ad Analytics.

Ad esempio, è possibile selezionare **[!UICONTROL poiname]** come chiave e **[!UICONTROL `{%%Last Entered POI Name}`.]

>[!TIP]
>
>È possibile impostare le regole di elaborazione di Analytics per recuperare i dati contestuali. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). Nell’esempio in *Creazione di un’azione*, l’azione invierà l’evento `poiname` come contesto per descrivere l’evento POIentry che viene inviato ad Analytics.

![creazione di un'azione](/help/assets/configure-action.png)

Esempio della regola completa:

![regola completata](/help/assets/create-a-rule.png)

## Creazione di un messaggio in-app in AMS

Come parte dei parametri di Trigger, puoi creare il pubblico per il messaggio con i dati provenienti da Location Service in uno dei modi seguenti:

* Utilizzo di azioni specifiche per la posizione, ad esempio una voce o un'uscita.
* Utilizzo di metadati POI inviati come dati contestuali per limitare la destinazione del pubblico.

   Questa opzione può essere utilizzata con un'azione specifica per una posizione, ad esempio una voce, o può essere utilizzata come contesto per un altro evento, ad esempio un avvio o un clic di pulsante.

   Di seguito è riportato un esempio di come configurare un messaggio in-app per accogliere gli utenti che immettono un POI con **[!UICONTROL Adobe]** il nome:

   ![parametri di attivazione](/help/assets/trigger-parameters.png)

* I parametri nelle intestazioni Luoghi della pagina *Triggers e Caratteristiche* di Mobile Services non funzionano con i dati di Location Service. Questi parametri sono solo per il database legacy di Places creato in Mobile Services.