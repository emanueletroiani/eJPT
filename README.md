# Salvare le nostre scan

-**oN** salva la scan esattamente come la stampa nmap, formato .txt

-**oX** formato xml per permettere a metasploit di leggere la scan

-**oG** salva la scan in un formato che permette di utlizzare il comando **grep**

-**oA** salve la scan nei formati -oN -oX -oG

# Prima fase

Capire se l’host è online e raggiungibile o quanti host ci sono in una rete tramite comandi ping:

Kali 

- **ping -c N° IP_TARGET** indica quanti pacchetti inviare al target

Windows

- **ping -n N° IP_TARGET** indica quanti pacchetti inviare al target

---

- **ping -b -c N° IP_RETE** manda pacchetto ad ogni host sulla rete target es: ping  -b -c 1 192.168.1.0
- **fping -a -g IP_RETE/SUBNET** pingare tutti gli host sulla rete ES fping -a -g 192.168.1.0/24
- **fping -a -g IP_RETE/SUBNET 2>/dev/null**  per eliminare l’elenco di ping agli IP offline

oppure possiamo utilizzare nmap

### **Per scansionare piu IP con un PING (vedere se host è online)**

- **nmap –sn TARGET_ip/CIDR**’
- -**sn**  non scansiona le porte ma permette di vedere se l’host **è online** senza inviare pacchetti di ping (si è invisibili)
- **nmap –sn 192.168.1.1-150** pinga gli ip nel range
- **nmap –sn 192.168.1.*** prende tutti gli ip
- **nmap –sn –iL file_ip.txt**  nmap scansiona gli IP all’interno del File

### Comandi

- **nmap -sn -PS IP_TARGET**
    - **-PS** se non specifichiamo niente dopo questo comando, manderà un pacchetto SYN alla porta 80
- **nmap -sn -PSN° IP_TARGET**
    - **-PS22** puoi decidere la porta dove nmap manderà il pacchetto (in questo caso 22
- **nmap -sn -PS1-1000 IP_TARGET (**MOLTO UTILE)
    - **-PS1-1000** dici  nmap di mandare i pacchetti SYN ad un range di porte tra 1 a 1000
- **nmap -sn -PSN°,N°,N° IP_TARGET**
    - **-PSN80,445,3389** puoi decide le porte
- **nmap -sn -PA IP_TARGET** (non raccomandato l’utlizzo)
    - **-PA** se non specifichiamo niente dopo questo comando, manderà un pacchetto ACK alla porta 80

### Comando da utilizzare per Host Discovery

- **nmap -sn -v -T4 IP_TARGET**
- **nmap -sn -PS IP_TARGET**
- **nmap -sn -PS21,22,25,80,445,3389,8080 IP_TARGET** migliore
- **nmap -sn -PS21,22,25,80,445,3389,8080 -PU137,138 IP_TARGET** da utilizzare piu’ su windows PU manda pacchetti UDP

# Seconda fase A

Determinare le porte aperte e le vulnerabilità

### nmap scansione le porte con le opzioni

**-p port,port,port**

-**p1-100** (per range di porte)

-**p-**

**-F** scansione le 100 porte piu comuni

Poi fa vedere nmap (**senza aggiungere opzioni ma facendolo partire come root**) di default per vedere se una porta è aperta manda un pacchetto Syn, se riceve una pacchetto SYN/ACK allora lo chiude inviando un pacchetto RST. cose gia viste

**-sT** TCP scansione porte tcp con 3ways hand shake

-**sU** UDP scansione porte UDP

**-sS** scansione SYN di porte TCP

### nmap scansione le vulnerabilità e rileva il sistema operativo con

-**sV** detection versione servizi

**-O** detection sistema operativo

**--osscan-guess** detection aggressiva del sistema operativo

**--version-intensity N** mettere un valore da 0 a 8 e serve per avere un’accuratezza della scansione dei servizi

Importante sapere che con questi comandi non è possibile sapere la distribuzione del SO

# Seconda fase B (se in presenza di firewall)

**-sA** avvia scansione con pacchetti ACK per vedere le porte sono filtrate fa firewall o IDS

**-f** Invia pacchetti frammentati

**--mtu N** imposta la grandezza del pacchetto con cui eseguirà la scansione (minimo 8 massimo 65536)

Spoofing:

**-D IP_RETE** Spoofing dei pacchetti con nmap, bisogna essere collegati alla rete target

**-n** non risolve i DNS

**-g** cambiare porta di origine dei pacchetti per rendere meno sospetti utilizzare la 53(DNS),123(NTP),443,80

**--data-lenght N°** viene utilizzata per aggiungere dati di riempimento (in byte) ai pacchetti inviati durante una scansione. 

# Terza fase

Utilizzare script nmap per acquisire info o eseguire exploit

è una caratteristica dello strumento nmap che permette di scrivere e condividere script per automatizzare un’ampia varietà di task come:

- scansione porte
- rilevamento della versione dei servizi
- scansione delle vulnerabilità
- sfruttamento delle vulnerabilità
- brute force
- etc..

nmap possiede una enorme varietà di script creati dalla community e di default. Sono accessibili nella cartella linux 

- **/usr/share/nmap/scripts**
- **ls -al /usr/share/nmap/scripts | grep -e ‘parola_da_cercare’** trovare script all’interno della cartella

hanno tutti l’estenzione **.nse** e sono suddivisi in categorie, discovery, exploitation, brute force, safe.

C’è poi un **categoria** che ci permette di **ingaggiare** il bersaglio **senza** impegnarci attivamente in **modo pericoloso** sfruttando le vulnerabilità automaticamente

**-sC** probabili vulnerabilità e distribuzione linux

se troviamo una vulnerabilità di un servizio possiamo cercare lo script nella cartella linux per vedere a che categoria appartiene e poi farlo partire

### Come trovo la categoria degli Script?

- **nmap --script-help=NOME_SCRIPT** stampa la categoria dello script

### Come utlizzare lo script

- **nmap** **--script=NOME_SCRIPT (senza estensione)** utilizza script selezionato
    - ESEMPIO: **nmap** **--script=ftp-anon -sS -sV -T4 -p- IP_TARGET**
- **nmap** **--script=NOME_SERVIZIO-***  avvia tutti gli scripts per quel servizio
    - ESEMPIO**: nmap** **--script=ftp-* -sS -sV -T4 -p- IP_TARGET**
    - 

Nel laboratorio finale è richiesta anche conoscenza di sql per trovare la flag:

## mySQL

- **mysql -u NOME_UTENTE -p -h HOST_TARGE**T
    - **-u** Specifica l'utente con cui accedere.
    - **-p** Chiede la password per l'utente specificato. Dopo aver eseguito il comando, MySQL richiederà l'inserimento della password (non visibile durante la digitazione).
    - **-h** Definisce l'host del server MySQL a cui connettersi.

Comandi una volta entrati

- **show databases;**

NOTA

- Se ometti **-h,** MySQL tenterà di connettersi al server locale (`localhost`).
- Se ometti **-p**, MySQL non richiederà una password (utile se il database non è protetto o si utilizza un accesso senza password).


