---
title: Notifiche in-app
description: Questa sezione illustra come utilizzare il servizio Places con i messaggi in-app.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 4%

---

# Notifiche in-app {#places-push-messaging}

Le informazioni seguenti mostrano come configurare i messaggi in-app da attivare dagli eventi del servizio Places.

>[!IMPORTANT]
>
>I messaggi devono trovarsi in un hit di Analytics.

## Messaggio in-app

Mobile Services consente di utilizzare i dati sulla posizione inviati ad Analytics come evento o condizione di attivazione per un messaggio in-app. Se i messaggi in-app vengono attivati dall’SDK e non è necessario attendere che i dati vengano elaborati da Analytics, i messaggi possono essere visualizzati in tempo reale non appena si verifica l’attivatore.

### Notifiche locali

Elenco dei tipi di messaggistica in-app disponibili:

* A schermo intero
* Avviso
* Notifiche locali

Questi tipi sono messaggi in-app perché vengono attivati dall&#39;SDK. Le notifiche locali hanno l&#39;aspetto e la sensazione di notifiche push perché vengono visualizzate quando l&#39;app è in background. Queste notifiche inviano anche notifiche in tempo reale quando gli utenti entrano o escono dai punti di interesse mentre l&#39;app è in background.

### Prerequisiti

Prima di iniziare, scopri come inviare e creare un messaggio in-app in Mobile Services e come funzionano gli attivatori. Per ulteriori informazioni, consulta [Creare un messaggio in-app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regole in Experience Platform Launch

Puoi creare regole di Experience Platform Launch che inviano ad Analytics i dati che desideri possano essere utilizzati come parte delle tue regole di attivazione dei messaggi in-app. Puoi utilizzare i dati delle estensioni Luoghi nelle regole del Experience Platform Launch come eventi e/o condizioni a seconda del caso d’uso.

* Utilizzo dei dati sulla posizione come evento che scatena l&#39;attivazione.

   Ad esempio, puoi inviare dati ad Analytics quando un utente accede a un POI.

* Utilizzo dei dati sulla posizione come condizione per attivare un evento.

   Ad esempio, se hai creato un tag di metadati personalizzato nel servizio Places per il tempo in diversi POI, puoi utilizzarli come parametro per la condizione Regola. Anche se è possibile utilizzare questa condizione con un evento POI entry descritto in precedenza, è anche possibile utilizzare la condizione come contesto per qualsiasi evento.

Una volta impostata la regola con i parametri di evento e condizione appropriati, completa la configurazione della regola configurando l’azione per l’invio di dati ad Analytics.

## Crea un&#39;azione

Per creare un&#39;azione:

1. Seleziona la **[!UICONTROL Adobe Analytics]** estensione.
1. In **[!UICONTROL Tipo di azione]** elenco a discesa, seleziona **[!UICONTROL Traccia.]**
1. Digita un nome per l’azione.
1. Nel riquadro a destra, in **[!UICONTROL Dati contestuali]**, seleziona la coppia chiave-valore per impostare i dati contestuali che verranno inviati ad Analytics.

Ad esempio, puoi selezionare `poiname` come chiave e `{%%Last Entered POI Name}` come valore.

>[!TIP]
>
>È possibile impostare le regole di elaborazione di Analytics per raccogliere questi dati contestuali. Per ulteriori informazioni, consulta [Regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). Nell’esempio in *Creare un’azione*, l&#39;azione invia `poiname` come contesto per descrivere l’evento POI entry che viene inviato ad Analytics.

![creazione di un&#39;azione](/help/assets/configure-action.png)

Ecco un esempio della regola completa:

![regola completata](/help/assets/create-a-rule.png)

## Creazione di un messaggio in-app in Mobile Services

Come parte dei parametri del trigger, puoi creare il pubblico per il messaggio con i dati del servizio Places in uno dei seguenti modi:

* Utilizzo di azioni specifiche per la posizione, ad esempio una voce o un&#39;uscita.
* Utilizzo dei metadati POI inviati come dati contestuali per limitare il target del pubblico.

   Questa opzione può essere utilizzata con un’azione specifica per una posizione, ad esempio un accesso, o può essere utilizzata come contesto per un altro evento, ad esempio un lancio o un clic su un pulsante.

   Ecco un esempio di come configurare un messaggio in-app per accogliere gli utenti che immettono un POI con **[!UICONTROL Adobe]** nel nome:

   ![parametri di attivazione](/help/assets/trigger-parameters.png)

* Parametri nelle intestazioni Servizio Luoghi nella *Triggers e caratteristiche* In Mobile Services non funziona con i dati di Places Service.

   Questi parametri sono solo per il database legacy di Places Service creato in Mobile Services.
