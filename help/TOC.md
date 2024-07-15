---
audience: end-user
user-guide-title: Guida di Places Service
user-guide-description: Places Service è un servizio di geolocalizzazione che consente alle app mobili che supportano la localizzazione di comprendere il contesto della posizione.
feature: Places
source-git-commit: 9f2c6fee6e0d6d075b662cc0b6cbee49cf05ee55
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 18%

---


# Servizio Places {#using}

+ [Panoramica di Places Service](home.md)
+ [Note sulla versione](release-notes.md)
+ [Introduzione](getting-started.md)
+ [Accedere a Places Service](places-gain-access.md)
+ Interfaccia utente di Places Service {#poi-mgmt-ui}
   + [Panoramica dell’interfaccia utente di Places Service](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Creare un POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [Gestire i POI creati in precedenza](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Strategie per l’utilizzo dei metadati con i punti di interesse](poi-mgmt-ui/metadata-with-pois.md)
   + [Caricamento in blocco di POI](poi-mgmt-ui/bulk-upload-pois.md)
   + [Gestire più librerie](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ API servizio Web {#web-service-api}
   + [Panoramica API del servizio web](web-service-api/places-web-services.md)
   + [Prerequisiti per l’integrazione](web-service-api/adobe-i-o-integration.md)
   + Utilizzo API {#api-usage}
      + [Panoramica sull’utilizzo delle API](web-service-api/api-usage/api-usage-overview.md)
      + [Intestazioni e parametri](web-service-api/api-usage/headers-and-parameters.md)
      + Gestisci librerie {#manage-libraries}
         + [Panoramica sulla gestione librerie](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [Creare una libreria](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Leggere una libreria](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Aggiornare una libreria](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Eliminare una libreria](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Leggi tutte le librerie della tua organizzazione](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Impostare una classificazione nelle librerie](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Ottieni il rango di una libreria](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Gestire i punti di interesse {#manage-pois}
         + [Panoramica sulla gestione dei punti di interesse](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Creare un POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [Leggi un POI](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [Aggiornare un POI](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Eliminare un POI](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Leggi tutti i POI in una libreria](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Leggi tutti i POI nell&#39;organizzazione](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + API batch {#batch-apis}
            + [Panoramica delle API batch](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Creare più punti di interesse](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Aggiornare più punti di interesse](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Eliminare più punti di interesse](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [API di query](web-service-api/api-usage/query-apis.md)
+ Estensioni per gli SDK di Mobile {#places-ext-aep-sdks}
   + [Estensione Luoghi](places-ext-aep-sdks/places-extension/places-extension.md)
+ [Utilizza Places Service con la tua soluzione di monitoraggio](using-your-own-monitor.md)
+ [Utilizza Places Service senza monitoraggio dell’area attiva](use-places-without-active-monitoring.md)
+ Utilizza Places Service come parte del flusso di lavoro di Experience Platform Launch {#use-places-launch-workflow}
   + [Utilizzare Places Service come parte del flusso di lavoro del Experience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [Definire gli elementi dati](use-places-launch-workflow/define-data-elements.md)
   + [Creare regole di entrata e di uscita](use-places-launch-workflow/create-rule-places-property.md)
+ Utilizza Places Service con altre soluzioni di Adobe {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Utilizzare Places Service con Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [Inviare dati di entrata e uscita POI ad Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Aggiungere contesto di posizione alle richieste di Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Rapporto sui dati relativi alla posizione in Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Notifiche push](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [Notifiche in-app](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Utilizzare Places Service con Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Notifiche push](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [Messaggi in-app](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Utilizzare Places Service con Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Test e convalida {#places-testing-validation}
   + [Test e convalida di Places Service](places-testing-validation/test-validate-places.md)
+ [Domande frequenti](places-faqs.md)
