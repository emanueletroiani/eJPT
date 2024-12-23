![Screenshot 2024-12-21 105438](https://github.com/user-attachments/assets/c7993f4e-365a-4ad3-bff6-f4df02b536c6)

E’ la prima fase del PN.

Serve per identificare ed ottenere Info su

- Web technology usate
- possibili Vulnerabilità
- IP address dell’Host
- gli Impiegati (ID o e-mail)

Si divide in Passiva e Attiva

- **Passiva**: siamo ancora nella legalità, sfruttiamo il web e tools OSINT
    - IP Addresses
    - DNS information
    - Nome del dominio e informazioni sulla proprietà del dominio
    - Email e profili social media
    - Subdomini
- **Attiva**: Coinvolgiamo attivamente il target (es nmap), abbiamo bisogno di un’autorizzazione
    - Scoprire Porte aperte
    - Imparare sulla strutta interna dell’ organizzazione/network target
    - Enumerazione informazioni del sistema target
  
# Passiva

## P-Website Recon & Footprinting

Cosa cerchiamo:

- IP Addresses
- Directories nascoste dai motori di ricerca
- Nomi
- Email
- Numeri di Cellulare
- Indirizzi Fisici
- Tecnologie web utilizzate

### IP Addresses

Da kali utilizziamo il comando **host DOMAIN_NAME** (hackerploit.org) per ottenere **IPv4, IPv6, email server**

Se ci sono **piu’** indirizzo **IP** è perchè l’host utilizza un servizio Firewall che contiene un **proxy** server (proxy server permette di navigare in rete un un altro IP)

### Directories nascoste dai motori di ricerca

Tutti i siti hanno un file di testo dove viene messo cio’ che il sito non vuole che venga trovato tramite i motori di ricerca. Per accedervi bisogna aggiungere **/robots.txt** all’indirizzo primario del sito

- **Disallow**: qui vengono messe le Directory da nascondere

### Sub Domini

Aggiungendo **/sitemap_index.xml** alla fine dell’indirizzo del sito otterremo tutti i sotto domini del sito. Sitemap serve per indicizzare al meglio le ricerche google del sito.

- utile per trovare anche pagine difficili da trovare da motori di ricerca.
- utile per trovare Nomi o email di autori di articoli

### Tecnologie Web utilizzate

Con l’estenzione firefox **BuiltWhit** è possibile ottenere Info sulle tecnologie utilizzate dalle pagine web .

Altri modi per ottenere le tecnologie utilizzare dalla web app possono essere l’estenzione firefox **Wappalyzer** e il comando da riga di comando **whatweb NOME_DEL_SITO** 

### SCARICARE UN INTERO SITO

Con il tools **HTTrack**

- Da Kali: **sudo apt-get install webhttrack**

## P-Whois enumeration

Si può utilizzare da riga di comando o direttamente dal sito **who.is**

- **whois NOME_SITO** da kali
    
- **whois IP_ADDRESS**
    - Con IP si otterranno molte piu info

### COSA CERCARE?

- Name server
    - Registrant State/Province
    - Registrant Organization
- Info DNS
    - DNSSEC
 
## P-Website Footprinting With Netcraft

Un [tool](https://www.netcraft.com/?utm_feeditemid=&utm_device=c&utm_term=netcraft&utm_source=google&utm_medium=ppc&utm_campaign=Google+%7C+Search+%7C+Brand+%7C+Exact+%7C+20221014&hsa_cam=18600605269&hsa_grp=150893442948&hsa_mt=e&hsa_src=g&hsa_ad=689927749890&hsa_acc=4527524350&hsa_net=adwords&hsa_kw=netcraft&hsa_tgt=kwd-514047884592&hsa_ver=3&gad_source=1&gclid=EAIaIQobChMIzILh18G2igMVEwcGAB2zCANbEAAYASAAEgL45vD_BwE) che serve per ottenere tutte le Info che abbiamo ottenuto precedentemente. In piu serve per enumerare info su certificati Web SSL o TLS.

### Info da cercare

- IPv4 (a volte non è il vero IP in quanto protetti da un proxy server)
- se ha un DNS security extensions
- Data scadenza Certificati SSL/TLS
- Firme dei Certificati
- Se è vulnerabile a **SSLv3/POODLE**
- Se è vulnerabile a **Heartbleed**
- Hosting History
- SSL Certificate Chain
- Web Trackers
- **HTTP Accelerator**: ci dice se c’è un proxy server abilitato
- Technology: le tecnologie in esecuzione nel sito
- Client-Side
- PHP Application: ci dice se il database è in esecuzione o è ospitato da un altro server

## P-DNS Recon

Sono istruzioni contenute nei server DNS e possiamo ottenerli tramite riga di comando su Kali

- **dnsrecon -d DOMAIN_NAME**

Da qui possiamo ottenere info come:

- **A:** Indirizzo IP
- **MX** : server di posta elettronica con relativo IP
    - (CloudeFlare proxy non nasconde questo IP del server di email))
- **NS**: Name server
- **SOA:** Memorizza info di amministrazione sul dominio

Oppure possiamo **utilizzare** il tool [**DNSdumpster**](https://dnsdumpster.com/) che organizza meglio queste info

## P-WAF With wafw00f

Questo tool ci permette di individuare i possibili WAF che proteggono il sito.

- **wafw00f DOMAIN_NAME**
- **wafw00f DOMAIN_NAME -a** cerca tutti i possibili WAF

## P-Subdomain Enumeration With Sublist3r

E’ un tools che serve per ottenere in modo passivo i Subdomini di un sito. Può anche eseguire Brute Force

**sudo apt-get install sublist3r** per installarlo

- **sublist3r -d DOMAIN_NAME**
- **sublist3r -d DOMAIN_NAME -e google,yahoo**
    - -**d**: ricerca i sottodomini
    - -**e**: utilizza i motori di ricerca selezionati

Con una VPN sorpassa i blocchi

## P-Google Dorks

- **site:WEB_DOMAIN inurl:admin** per cercare all’interno del sito web o all’interno dell’URL se c’è una pagine da Amministratore
- **site:*.WEB_DOMAIN** enumerare i sottodomini
- **site:*.WEB_DOMAIN**  **inurl:admin** sottodominio da Amministratore
- **site:*.WEB_DOMAIN**  **intitle:admin** sottodominio da Amministratore contenuti nel titolo
- **site:*.WEB_DOMAIN**  **filetype:pdf** all’interno dei sottodominio cerca file pdf
- **site:*.WEB_DOMAIN**  **filetype:xlsx** all’interno dei sottodominio cerca file xlsx
- **site:*.WEB_DOMAIN**  **filetype:doc**
- **site:*.WEB_DOMAIN**  **filetype:zip**
- **site:*.WEB_DOMAIN**  **filetype:jpg**

Ricerche sui dipendeti

- **site:WEB_DOMAIN employees**
- **site:WEB_DOMAIN** **instructors**

Vedere Directory

- **site:WEB_DOMAIN intitle:index of** mostra le directory (se vulnerabile)

Vedere il sito come era giorni o mesi prima

- **waybackmachine** sito web che lo permette

Directory con password

- **inurl:auth_user_file.txt**
- **inurl:password.txt**
- **intitle:password.txt**

### BEST SITO PER DORKS

https://www.exploit-db.com/google-hacking-database

- **file containing passwords** è un filtro che mostra dorks per la ricerca di pass
- **wp** in quick search mostra dorks di wordpress

## P-Email Harvesting With theHarvester

Tool molto potente e molto utilizzato per ottenere emails, nomi, subdomini, IP e URL

Preinstallato su Kali, ecco alcuni comandi

- **theHarvester -d DOMAIN_NAME -l 100 -b FONTE,ALTRA FONTE** (fonti ma mettere su si trovano [qui](https://github.com/laramies/theHarvester) sotto la voce passive)
    - -**d** target dominio
    - -**l** (L minuscola) massimo 100 risultati
    - **-b** fonte da cui prendere i dati

Tra le diverse fonti da utilizzare va bene **yahoo** ma **spyse**  è ottimo pero’ richiede un abbonamento

##  P-Leaked Password Databases

Con [questo](https://haveibeenpwned.com/) sito, possiamo sapere se i dati delle email che abbiamo trovato in precedenza possono far parte di un Leak.

## A-DNS Zone Transfers

### DNS Records

- **A** - Risolve un hostname o un dominio per un IPv4
- **AAAA** - Risolve un hostname o un dominio per un IPv6
- **NS** - Si riferisce al nome del server del dominio
- **MX** - Risolve un dominio per il mail server
- **CNAME** - Usato per gli alias di dominio
- **TXT** - IL file di testo dei records
- **HINFO** - Informazioni dell’ Host
- **SOA** - L’autorità del dominio
- **SRV** - Il record dei servizi
- **PTR** - Risoluzione di un IP per un hostname

### Come ottenere piu records da un DNS di un dominio?

**ZONE TRASFER**: In alcuni casi gli amministratori dei server DNS potrebbero voler copiare o trasferire file di zone tra un server DNS ad un altro. 

Se configurato male e non protetto:

- Si possono attaccare per copiare file di zona dal DNS primario ad un altro server DNS
- Può fornire una visione dello schema della rete di un’roganizzazione
- Si possono trovare sottodomini

### [Fonte per studiare zonetrasfert](https://digi.ninja/projects/zonetransferme.php)

### Host File

E’ conservato in questa directory **nano /etc/hosts**  a qui possiamo vedere la risoluzione dei domini all’interno di un host. per esempio possiamo modificare il nostro IP locale con una stringa di caratteri

In questo modo se digitiamo nel browser **router.admin** ci aprirà quell’indirizzo IP

### dnsenum

Enumera il DNS target, è un tool linux, in automatico fa partire anche un bruteforce per accedere a questo file **/usr/share/dnsenum/dns.txt** 

Da kali la stringa è la seguente

- **dnsenum DOMAIN_NAME**

Con questo tool potremo sapere come è strutturata la rete web del sito, con sottodomini interni e sottodomini accessibili da internet

### fierce

è un tool che permette di ottenere le zone transfert con bruteforce, è meglio di dnsenum 

- **fierce -dns DOMAIN_NAME**

### [Comando Dig](https://www.naosdata.com/blog/2023/dig-tool-dns-senza-segreti.php)

l **comando** **Linux dig** (*Domain Information Groper*) è un potente strumento che può essere usato per interrogare un server DNS e ottenere diverse informazioni su un dominio. Si capisce subito quindi che è un comando che può essere estremamente utile sia per gli amministratori di rete che per gli sviluppatori web.

Usando dig si può risalire a informazioni come:

- Risolvere i nomi di dominio in indirizzi IP e viceversa
- Eseguire ricerche DNS su un determinato tipo di record come MX, NS, TXT, etc.
- Ottenere informazioni sui server DNS di un determinato dominio
- Verificare la risoluzione dei nomi di dominio da parte dei server DNS.

## A-Host Discovery With Nmap

- **ip a** ip su eth0 è il nostro. se mettiamo la rete su nmap possiamo vedere gli indirizzi connessi.
    - ES:
    - **eth0 10.0.2.15/24**
    - **sudo nmap -sn 10.0.2.0/24** per vedere host connessi

### nmap

- **-sn** no port scan, si limita a trovare gli host su di una rete senza andare alla ricerca di porte aperte (ping scan)

### netdiscover

- **sudo netdiscover -i eth0 -r IP_INDIRIZZO_RETE**

## A-Port Scanning With Nmap

I sistemi windows bloccheranno le ricerche ICMP fatte con nmap evitare questo, utilizziamo l’opzione **-Pn** prende il target come online sulla rete.

Alcune porte possono essere filtrate da un proxy

- **-p-** scan di tutte le porte
- **-p 80,443,23** scan delle porte richieste
- **-p1-10000** scan dell porte da 1 a 10000
- **-F** fast scan
- **-sU** udp scan
- -**sV** enumera i servizi sulle porte
- **-O** enumera il sistema operativo (non molto accurato)
- -**sC** enumera piu info tramite script di default nmap
- **-A** enumera sistema operativo + script default nmap (-sV -O -sC tutti insieme)
- **-T** indica la velocita’ con cui viene fatta la scan
    - T0 Paranoid
    - T1 sneaky
    - T2 polite
    - T3 Normal
    - T4 Aggressive
    - T5 insane
- **oN** **file.txt** salva i risultati della scan nel file
- **oX file.xml** utile per salvare ed importare la ricerca su file in metasploit







