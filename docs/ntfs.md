---
layout: page
title: Leggere e scrivere volumi ntfs con macos gratuitamente
permalink: /ntfs/
---

Controllare come prima cosa lo stato del SIP con il comando “csrutil status”, la risposta che si dovrebbe ottenere è “System Integrity Protection status: disabled.” In caso contrario si deve modi care la EFI in maniera da disattivare il SIP oppure entrare in recovery e disattivarlo tramite terminale utilizzando il comando “csrutil disable”.

1.	Scaricare e installare FUSE for Mac. È il programma che consente di estendere le capacità di gestione dei File System nativi tramite applicazioni di terze parti . https://osxfuse.github.io

2. Installare Homebrew copiando la riga di comando che in https://brew.sh e incollare sul Terminal. Homebrew è un gestore pacchetti aggiuntivo che permetterà di scaricare e installare NTFS-3G.

3. Installare NTFS-3G lanciando il comando

```brew install ntfs-3g```

E’ ora possibile utilizzare FUSE a MacOS per montare i volumi ntfs, sostituendo il  le che usa nativamente MacOS con un collegamento a FUSE.

### Effettuare il mount il lettura e scrittura del nostro disco
```sudo mount -uw /```

Rinominare il file che usa nativamente MacOS da mount_ntfs a mount_ntfs.ori cosi da permettere la sostituzione del  le con il collegamento, conservando un backup da ripristinare in caso di problemi.

```sudo mv /Volumes/TUODISCO/sbin/mount_ntfs /Volumes/TUODISCO/sbin/mount_ntfs.ori```

Creare un link simbolico al file installato dal pacchetto ntfs-3g, nel percorso dove macos si aspetta di avere il suo programma per montare il file system NTFS.

```sudo ln -s /usr/local/sbin/mount_ntfs /Volumes/TUODISCO/sbin/mount_ntfs```

Se non sono pervenuti messaggi di errore è possibile ora provare a mettere una chiavetta formattata ntfs e vedere se viene montata con FUSE.

E’ possibile che con degli aggiornamenti di MacOS il link venga sovrascritto dai file originali per cui potrebbe essere necessario rifare le ultime 3 operazioni con il terminale per ripristinare il funzionamento.


