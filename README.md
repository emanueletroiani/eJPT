# Port Scanning with Auxiliary Modules

I **moduli ausiliari** servono per **identificare Host**, **porte** aperte, **servizi** etc come i comandi lanciati precedentemente con nmap ma la grande differenza è che con i moduli ausiliari possiamo fare del **pivoting**, ovvero una volta che avremo accesso ad un host su di una rete target potremo utilizzarlo per scansionare con moduli ausiliari un altro target.

I moduli ausiliari possono essere eseguiti durante la fase di post-sfruttamento sulle reti interne.

AVVIO STANDARD DI METASPLOIT

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **search portscan**
5. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano

# FTP

Utilizza la **porta 21**, il suo compito è di facilitare il trasferimento di file tra server e client to clients.

Utilizzato anche per il **trasferimento** di file **da** e **tra** le **directory** di un **web** server

Per enumerarlo ci sono diversi auxiliary come i bruteforce in quanto utilizza delle credenziali di accesso vulnerabile anche ad anoniymous

# SMB

Samba è il **protocollo** utilizzato per **condividere** i **file** tra host in una rete **locale.** Di default utilizza porta **445 TCP** sui nuovi dispositivi Windows porta **139 NETBios**

Samba è stato implementato da Linux per permettere ai sistemi windows di accedere alle cartelle e dispositivi.

Permette anche agli **utenti** di **connettersi** alle **stampanti**

# Web Server

Un **Web server** è un **software** che viene utilizzato per servire i dati di un sito web nella rete web.

**Utilizza** il protocollo **HTTP** per facilitare le comunicazioni tra clients e web server.

**Famosi** Web server sono **Apache**, **Nginx** e **Microsoft IIS**

### Qual’è il processo di apertura di una pagina web

1. digitiamo il sito HTTP/HTTPS nel browser
2. Il DNS risolverà il nome del dominio in un IP con una ricerca nelle sue tabelle di IP
3. il server web invierà una richiesta HTTP di risposta al Browser contenente generalmente info come dati del sito web

# MySQL

MySQL è un **database relazionale** open source di **gestione** basato su **linguaggio SQL**

Viene utilizzato per **memorizzare** i **dati** delle applicazioni web, esse contengono anche dati dei clienti come pass ed username.

Utilizza la **porta 3306** di default.

# SSH Enumeration

Il **protocollo SSH (Secure Shell)** è un protocollo di rete crittografato utilizzato per stabilire una **connessione** sicura **tra due** **macchine**, tipicamente un client e un server. **SSH** fornisce un **metodo sicuro** per **accedere** e **gestire** **sistemi remoti** attraverso una rete non sicura, come Internet, consentendo **l’esecuzione** di **comandi**, il **trasferimento** di **file**, il **tunneling** e altro, proteggendo la riservatezza e l'integrità dei dati tramite crittografia.

Di default utilizza la **porta 22**

# SMTP Enumeration

SMTP è un **protocollo** di **comunicazione** utilizzato per l’invio di **email**

Utilizza la **porta** TCP **25** di default, può essere configurato anche nella porta **465** e **587 se** criptata da **ssl/tls**



