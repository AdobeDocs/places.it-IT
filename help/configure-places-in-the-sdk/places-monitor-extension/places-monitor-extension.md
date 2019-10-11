---
title: Estensione Luoghi monitor
seo-title: Estensione Luoghi monitor
description: L’estensione Places Monitor gestisce le interazioni con il sistema operativo per registrare e monitorare i POI più vicini all’utente.
seo-description: 'L’estensione Places Monitor gestisce le interazioni con il sistema operativo per registrare e monitorare i POI più vicini all’utente. '
translation-type: tm+mt
source-git-commit: a785b75ccbed2a62d0e9f77b5c17dae9447b0629

---


# Estensione Luoghi monitor {#places-monitor-extension}

L’estensione Places Monitor gestisce le interazioni con il sistema operativo per registrare e monitorare i POI più vicini all’utente. Questa estensione recupera i POI che devono essere registrati dall’estensione Luoghi e trasmette le notifiche di entrata e uscita all’estensione Luoghi. Queste notifiche saranno disponibili nelle regole Experience Platform Launch come eventi.

L'estensione del monitor è opzionale, perché alcuni clienti potrebbero già essere regioni di monitoraggio con il sistema operativo. In questo caso, accertatevi di aggiungere le API di estensione Places per ricevere i POI più vicini dal database Places e per passare anche gli eventi di entrata e uscita in modo da poter eseguire le azioni appropriate.
