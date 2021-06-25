---
title: Estensione Monitor Luoghi
description: L’estensione Monitor Luoghi gestisce le interazioni con il sistema operativo per registrare e monitorare i punti di interesse più vicini all’utente.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Estensione Monitor Luoghi {#places-monitor-extension}

L’estensione Monitor Luoghi gestisce le interazioni con il sistema operativo per registrare e monitorare i punti di interesse più vicini all’utente. Questa estensione recupera i POI che devono essere registrati dall’estensione Places e trasmette le notifiche di entrata e uscita all’estensione Places. Queste notifiche saranno disponibili nelle regole del Experience Platform Launch come eventi.

L&#39;estensione Monitor è opzionale, perché alcuni clienti potrebbero già monitorare aree con il sistema operativo. In questo caso, accertati di aggiungere le API di estensione Luoghi per ricevere i POI più vicini dal database di Places Service e di passare anche gli eventi di entrata e uscita in modo da poter intraprendere le azioni appropriate.

## Obsolescenza monitor Luoghi

Il 31 agosto 2021 l’estensione Monitor Luoghi per gli SDK di Adobe Experience Platform Mobile diventerà obsoleta. L’estensione Monitor Luoghi non riceverà ulteriori aggiornamenti o supporto oltre il 31 agosto.

I clienti che attualmente utilizzano l’estensione Monitor Luoghi possono continuare a utilizzare questa estensione purché non siano disponibili aggiornamenti o supporto aggiuntivi tramite Adobe.

La deprecazione dell’estensione Monitor Luoghi non ha alcun impatto negativo o negativo sull’estensione Servizio Luoghi che continuerà a essere supportata con miglioramenti e aggiornamenti.

I clienti che desiderano passare dall’estensione Monitor Luoghi alla propria soluzione di monitoraggio devono consultare la documentazione relativa a: [Utilizza Places Service con la tua soluzione di monitoraggio](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). Questo documento spiega come interagire con il servizio Places implementando [Servizi di posizione core](https://developer.apple.com/documentation/corelocation) su iOS o [Location Services](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) da Google Play.
