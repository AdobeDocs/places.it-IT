---
title: Notifiche in-app
description: Questa sezione illustra come utilizzare Places Service con la messaggistica in-app.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Notifiche in-app {#places-push-messaging}

Le informazioni seguenti mostrano come configurare i messaggi in-app per l’attivazione dagli eventi di Places Service.

>[!IMPORTANT]
>
>I messaggi devono trovarsi in un hit di Analytics.

## Messaggio in-app

Mobile Services consente di utilizzare i dati sulla posizione inviati ad Analytics come evento/i di attivazione e/o condizione per un messaggio in-app. Se i messaggi in-app vengono attivati dall’SDK e non devono attendere l’elaborazione dei dati da parte di Analytics, possono essere visualizzati in tempo reale non appena si verifica l’evento di attivazione.

### Notifiche locali

Elenco dei tipi di messaggistica in-app disponibili:

* A schermo intero
* Avviso
* Notifiche locali

Questi tipi sono messaggi in-app perché sono attivati dall’SDK. Le notifiche locali hanno l’aspetto di notifiche push, in quanto vengono visualizzate quando l’app è in background. Queste notifiche forniscono anche notifiche in tempo reale quando gli utenti entrano o escono dai punti di interesse mentre l’app è in background.

### Prerequisiti

Prima di iniziare, scopri come inviare e creare un messaggio in-app in Mobile Services e come funzionano i trigger. Per ulteriori informazioni, vedere [Creare un messaggio in-app.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=it)

## Regole nel Experience Platform Launch

Puoi creare regole di Experience Platform Launch che inviano ad Analytics i dati che desideri possano essere utilizzati come parte delle regole del trigger dei messaggi in-app. Puoi utilizzare i dati delle estensioni Luoghi nelle regole del Experience Platform Launch come eventi e/o condizioni a seconda del caso d’uso.

* Utilizzo dei dati sulla posizione come evento che attiva.

  Ad esempio, puoi inviare dati ad Analytics quando un utente entra in un POI.

* Utilizzo dei dati sulla posizione come Condizione per un evento che si attiva.

  Ad esempio, se hai creato un tag di metadati personalizzato nel servizio Places per il meteo in punti di interesse diversi, puoi utilizzarlo come parametro per la condizione della regola. Anche se è possibile utilizzare questa condizione con un evento di ingresso POI descritto in precedenza, è anche possibile utilizzarla come contesto per qualsiasi evento.

Dopo aver configurato la regola con i parametri evento e condizione corretti, completa la configurazione della regola configurando l’azione per inviare dati ad Analytics.

## Crea un&#39;azione

Per creare un&#39;azione:

1. Seleziona l&#39;estensione **[!UICONTROL Adobe Analytics]**.
1. Nell&#39;elenco a discesa **[!UICONTROL Tipo azione]**, selezionare **[!UICONTROL Traccia.]**
1. Digita un nome per l’azione.
1. Nel riquadro di destra, in **[!UICONTROL Dati contestuali]**, selezionare la coppia chiave-valore per impostare i dati contestuali che verranno inviati ad Analytics.

Ad esempio, è possibile selezionare `poiname` come chiave e `{%%Last Entered POI Name}` come valore.

>[!TIP]
>
>Le regole di elaborazione di Analytics possono essere impostate per raccogliere questi dati contestuali. Per ulteriori informazioni, vedere [Regole di elaborazione](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=it). Nell&#39;esempio in *Crea un&#39;azione*, l&#39;azione invierà `poiname` come contesto per descrivere l&#39;evento di ingresso POI inviato ad Analytics.

![creazione di un&#39;azione](/help/assets/configure-action.png)

Ecco un esempio della regola completa:

![regola completata](/help/assets/create-a-rule.png)

## Creazione di un messaggio in-app in Mobile Services

Come parte dei parametri Trigger, puoi creare il pubblico per il messaggio con i dati del servizio Places in uno dei seguenti modi:

* Utilizzo di azioni specifiche per la posizione, ad esempio una voce o un&#39;uscita.
* Utilizzare i metadati dei punti di interesse inviati come dati contestuali per limitare il target del pubblico.

  Questa opzione può essere utilizzata con un’azione specifica per la posizione, ad esempio una voce, oppure come contesto per un altro evento, ad esempio un lancio o un clic su un pulsante.

  Di seguito è riportato un esempio di come configurare un messaggio in-app per accogliere gli utenti che immettono un POI il cui nome contiene **[!UICONTROL Adobe]**:

  ![parametri trigger](/help/assets/trigger-parameters.png)

* I parametri nelle intestazioni del servizio Places nella pagina *Triggers e caratteristiche* in Mobile Services non funzionano con i dati del servizio Places.

  Questi parametri valgono solo per il database legacy di Places Service creato in Mobile Services.
