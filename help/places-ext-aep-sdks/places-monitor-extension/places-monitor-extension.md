---
title: Estensione Luoghi monitor
description: L’estensione Places Monitor gestisce le interazioni con il sistema operativo per registrare e monitorare i POI più vicini all’utente.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Estensione Luoghi monitor {#places-monitor-extension}

L’estensione Places Monitor gestisce le interazioni con il sistema operativo per registrare e monitorare i POI più vicini all’utente. Questa estensione recupera i POI che devono essere registrati dall’estensione Luoghi e trasmette le notifiche di entrata e uscita all’estensione Luoghi. Queste notifiche saranno disponibili nelle regole Experience Platform Launch come eventi.

L&#39;estensione del monitor è opzionale, perché alcuni clienti potrebbero già essere regioni di monitoraggio con il sistema operativo. In questo caso, accertatevi di aggiungere le API delle estensioni Places per ricevere i POI più vicini dal database di Places Service e di passare anche gli eventi di entrata e uscita in modo da poter eseguire le azioni appropriate.
