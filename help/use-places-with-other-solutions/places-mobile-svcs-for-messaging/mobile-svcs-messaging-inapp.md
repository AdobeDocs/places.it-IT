---
title: Messaggistica in-app
seo-title: Messaggistica in-app
description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi in-app.
seo-description: In questa sezione viene illustrato come utilizzare i Luoghi con i messaggi in-app.
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# Notifiche in-app (#place-push-messaging)

Come configurare i messaggi in-app per l'attivazione dagli eventi Luoghi; i messaggi devono trovarsi in un hit Analytics.

## Messaggio in-app

AMS consente di utilizzare i dati sulla posizione che vengono inviati ad Analytics come evento o condizione di attivazione per un messaggio in-app. I messaggi in-app possono essere visualizzati all'utente in tempo reale non appena l'attivatore viene attivato dall'SDK e non è necessario attendere che i dati vengano elaborati da Analytics.

Notifiche locali: La messaggistica in-app ha 3 tipi diversi:

* A schermo intero
* Avviso
* Notifiche locali.

Questi tipi si qualificano come messaggi in-app perché vengono attivati dall'SDK, ma è importante notare che le notifiche locali appaiono come notifiche push mentre appaiono mentre l'app non è in primo piano. Le notifiche locali sono un’ottima opzione per inviare notifiche in tempo reale agli utenti quando entrano o escono dai POI mentre l’app è in background. Per informazioni sul monitoraggio della posizione (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension), consultate la documentazione relativa all’estensione del monitor Luoghi.

### Prerequisiti

* Scopri come inviare e creare un messaggio in-app in AMS e come funzionano gli attivatori.

   Per ulteriori informazioni, consulta [Creare un messaggio in-app](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Creare una regola in Experience Platform Launch

Crea regole di avvio che invia ad Analytics i dati corretti da utilizzare come parte delle regole di attivazione messaggi in-app. Puoi utilizzare i dati delle estensioni Luoghi nelle regole di Launch come eventi e/o condizioni a seconda del caso d’uso.

* Utilizzo dei dati sulla posizione come evento di attivazione. Ad esempio, se desiderate inviare dati ad Analytics quando un utente inserisce un POI.

* Utilizzo dei dati della posizione come condizione per un evento di attivazione. Ad esempio, se avete creato un tag di metadati personalizzato in Location Service per il tempo in diversi POI, potete utilizzare tali metadati come parametro per la condizione Regola come illustrato di seguito. Sebbene sia possibile utilizzare questa condizione per utilizzare l’evento voce POI descritto in precedenza, è anche possibile utilizzarla come contesto per qualsiasi evento.

Una volta impostata la regola con i parametri di evento e condizione corretti, completate la configurazione della regola configurando l'azione per l'invio di dati ad Analytics. Per eseguire questa operazione:

* Selezionate Adobe Analytics come estensione
* Scegliete "Track" come tipo di azione
* Determinare un nome per l’azione
* Impostate i dati contestuali in modo che vengano inviati con l’evento. Utilizza l’interfaccia Dati contestuali per mappare Launch Data Elements ai nomi chiave che desideri inviare ad Analytics.

È possibile impostare le regole di elaborazione di Analytics per recuperare i dati contestuali. Se necessario, consultate Regole di elaborazione di Analytics (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)Ad esempio, questa azione viene inviata nel nome del puntatore come contesto per descrivere l’evento POIentry che viene inviato ad Analytics.

![creazione di un'azione](/help/assets/configure-action.png)

Ecco un esempio di come potrebbe essere la regola finale.

![regola completata](/help/assets/create-a-rule.png)

## Creazione di un messaggio in-app in AMS:

Creerai l'audience per il messaggio con i dati del servizio di localizzazione come parte dei parametri Trigger.

* Utilizzo di azioni specifiche per la posizione, ad esempio entrata o uscita
* Utilizzo dei metadati POI inviati come dati contestuali per limitare la destinazione del pubblico. Può essere utilizzato con un'azione specifica per una posizione, ad esempio un ingresso, o può essere utilizzato come contesto per un altro evento, ad esempio un clic su un lancio o un pulsante.

   Di seguito è riportato un esempio di come impostare un messaggio in-app per dare il benvenuto agli utenti che immettono un POI con "Adobe" nel nome:

   ![parametri di attivazione](/help/assets/trigger-parameters.png)

* I parametri trovati nelle intestazioni "Luoghi" di attivatori e caratteristiche AMS non funzionano con i dati del servizio di localizzazione. Tali parametri sono per il database legacy Places creato in AMS.