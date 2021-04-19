---
audience: end-user
user-guide-title: Guida di Places Service
user-guide-description: Places Service è un servizio di geolocalizzazione che consente alle app mobili che supportano la localizzazione di comprendere il contesto della posizione.
translation-type: tm+mt
source-git-commit: 12283d11829ee70a808bc11d2bc1241cb1770ac3
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 19%

---


# Places Service {#using}

+ [Panoramica di Places Service](home.md)
+ [Note sulla versione](release-notes.md)
+ [Introduzione](getting-started.md)
+ [Accesso al servizio Places](places-gain-access.md)
+ Interfaccia utente di Places Service {#poi-mgmt-ui}
   + [Panoramica dell’interfaccia utente di Places Service](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Creare un POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [Gestire i POI creati in precedenza](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Strategie per l’utilizzo dei metadati con i POI](poi-mgmt-ui/metadata-with-pois.md)
   + [Caricamento in serie di POI](poi-mgmt-ui/bulk-upload-pois.md)
   + [Gestire più librerie](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ API del servizio Web {#web-service-api}
   + [Panoramica API del servizio Web](web-service-api/places-web-services.md)
   + [Prerequisiti per l’integrazione](web-service-api/adobe-i-o-integration.md)
   + Utilizzo API {#api-usage}
      + [Panoramica sull’utilizzo dell’API](web-service-api/api-usage/api-usage-overview.md)
      + [Intestazioni e parametri](web-service-api/api-usage/headers-and-parameters.md)
      + Gestire le librerie {#manage-libraries}
         + [Panoramica sulla gestione delle librerie](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [Crea una libreria](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Leggi una libreria](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Aggiornare una libreria](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Eliminare una libreria](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Leggi tutte le librerie nella tua organizzazione](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Imposta un rango sulle librerie](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Ottieni il rango di una biblioteca](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Gestire i punti di interesse {#manage-pois}
         + [Panoramica sulla gestione dei punti di interesse](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Creare un POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [Leggi un POI](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [Aggiornare un POI](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Eliminare un POI](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Leggi tutti i POI in una libreria](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Leggi tutti i punti di interesse nella tua organizzazione](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + API batch {#batch-apis}
            + [Panoramica delle API batch](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Creare più POI](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Aggiornare più POI](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Eliminare più POI](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [API di query](web-service-api/api-usage/query-apis.md)
+ Estensioni per gli SDK di Mobile {#places-ext-aep-sdks}
   + Estensione Luoghi {#places-extension}
      + [Estensione Luoghi](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Riferimento API per Luoghi](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Riferimento evento Luoghi](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Oggetti Luoghi personalizzati](places-ext-aep-sdks/places-extension/cust-places-objects.md)
   + Estensione Monitor Luoghi {#places-monitor-extension}
      + [Estensione Monitor Luoghi](places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)
      + [Utilizzo dell’estensione Monitor Luoghi](places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)
      + [Riferimento API di Monitor di Luoghi](places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.md)
+ [Utilizzare Places Service con la propria soluzione di monitoraggio](using-your-own-monitor.md)
+ [Utilizzare il servizio Places senza monitoraggio dell&#39;area attiva](use-places-without-active-monitoring.md)
+ Utilizza Places Service come parte del flusso di lavoro del Experience Platform Launch {#use-places-launch-workflow}
   + [Utilizzare Places Service come parte del flusso di lavoro del Experience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [Definire gli elementi dati](use-places-launch-workflow/define-data-elements.md)
   + [Creare regole di entrata e di uscita](use-places-launch-workflow/create-rule-places-property.md)
+ Utilizzare il servizio Places con altre soluzioni Adobe {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Utilizzare il servizio Places con Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [Inviare dati di entrata e uscita POI ad Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Aggiungere contesto di posizione alle richieste di Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Report sui dati sulla posizione in Analysis Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Notifiche push](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [Notifiche in-app](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Utilizzare il servizio Places con Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Notifiche push](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [Messaggi in-app](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Utilizzare il servizio Places con Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Test e convalida {#places-testing-validation}
   + [Test e convalida del servizio Places](places-testing-validation/test-validate-places.md)
+ [Domande frequenti](places-faqs.md)
