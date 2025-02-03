## With Nmap 

**-p port,port,port**

-**p1-100** (per range di porte)

-**p-**

**-F** scansione le 100 porte piu comuni

Poi fa vedere nmap (**senza aggiungere opzioni ma facendolo partire come root**) di default per vedere se una porta è aperta manda un pacchetto Syn, se riceve una pacchetto SYN/ACK allora lo chiude inviando un pacchetto RST. cose gia viste

**-sT** TCP scansione porte tcp con 3ways hand shake

-**sU** UDP scansione porte UDP

**-sS** scansione SYN di porte TCP

### Service Version & OS Detection

**-sV** detection versione servizi

**-O** detection sistema operativo

**--osscan-guess** detection aggressiva del sistema operatativo

**--version-intensity N** mettere un valore da 0 a 8 e serve per avere un’accuratezza della scansione dei servizi

Importante sapere che con questi comandi non è possibile sapere la distribuzione del SO

## Nmap Scripting Engine (NSE)

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
    - ESEMPIO: **nmap** **--script=ftp-anon -sS -sV -T4 IP_TARGET**
- **nmap** **--script=NOME_SERVIZIO-***  avvia tutti gli scripts per quel servizio
    - ESEMPIO**: nmap** **--script=ftp-* -sS -sV -T4 -p- IP_TARGET**
 
## Firewall Detection & IDS Evasion

Nmap ci da la possibilità di capire se l’host target è protetto da un Firewall o da un sistema di filtraggio. Esistono alcune opzioni che ci permettono di evadere i sistemi di monitoraggio delle reti o a mascherare la nostra identità.

**-sA** avvia scansione con pacchetti ACK per vedere le porte sono filtrate fa firewall o IDS

Un **altro modo** per eludere è inviare pacchetti **frammentati** con l’opzione **-f** in questo caso su wireshark possiamo notare che i pacchetti catturati mentre si sta analizzando la scansione di nmap, risultano con la dicitura Fragment IP Protocol

![image](https://github.com/user-attachments/assets/a4d90819-9655-4178-9df3-5d78acaf36c7)


**-f** Invia pacchetti frammentati

Alcune reti possono avere impostato come sicurezza un valore minimo di pacchetti che ricevono (VPN e Tunneling), per bypassare questo possiamo utilizzare --mtu che imposterà il valore in byte del pacchetto

**--mtu N** imposta la grandezza del pacchetto con cui eseguirà la scansione (minimo 8 massimo 65536)

## Fare spoofing con nmap

Ovvero facciamo risultare che nmap stia scansionando con l’IP del gateway di rete. per farlo dobbiamo essere connessi alla rete target

**-D IP_RETE** Spoofing dei pacchetti con nmap, bisogna essere collegati alla rete target

**-n** non risolve i DNS

**-g** cambiare porta di origine dei pacchetti per rendere meno sospetti utilizzare la 53(DNS),123(NTP),443,80

**--data-lenght N°** viene utilizzata per aggiungere dati di riempimento (in byte) ai pacchetti inviati durante una scansione.

## Optimizing Nmap Scans

A volte c’è necessità di rallentare le scan o velocizzarle, perchè?

Rallentare:

- per avere meno sospetti da **sistemi di sicurezza**
- per non provocare DoS su sistemi con hardware vecchi

nmap da la possibilità di **scegliere** quanto **tempo scansionare** un singolo **IP** per analizzarlo con le opzioni da noi inserite, piu è breve il tempo e meno risultati avremo ma avremo minor possibilità di essere riconosciuti dai sistemi di sicurezza. Se stiamo scansionando una rete finito il TIME da noi impostato poi passerà ad un altro

**--host-timeout TIME** permette di eseguire una scansione di un ip ogni Tot tempo che scegliamo noi. 

ES: **nmap --host-timeout 30s 10.10.10.10/24**

nmap permette anche di impostare un **delay tra** l’ invio di ogni **singolo pacchetto**, in questo modo potremo facilmente risultare non pericolosi ai sistemi di sicurezza

**--scan-delay TIME**

ES: **nmap --scan-delay 15s 10.10.10.10**

**Queste opzioni insieme ad altre determinano le opzioni T0-5**

## Salvare scan + integrazione nmap con Metaploit

Utilissimo quando le nostre scansioni impiegano molto tempo e dobbiamo visualizzarle piu volte.

-**oN** salva la scan esattamente come la stampa nmap, formato .txt

-**oX** formato xml per permettere a metasploit di leggere la scan

-**oG** salva la scan in un formato che permette di utlizzare il comando **grep**

-**oA** salve la scan nei formati -oN -oX -oG

### Perchè caricare le nostre scan su metasploit

Meta prende tutti i dati delle scan di nmap e le fa sue per i successivi utilizzi, in piu salva il file xml caricato nel suo database in modo che possiamo sempre accerdervi

### Come carico il file scan .xml su metasploit?

1. metasploit necessita che il servizio di database **postgresql** sia attivo
    1. **service postgresql start** 
2. su meta aggiungiamo un workspace
    1. **workspace -a NOME_WORKSPACE**
3. check sullo stato del database se è connesso a postgresql
    1. **db_status**
4. importiamo nel database la scan nmap
    1. **db_import FILE.xml**

ES comandi:

- **hosts** info su hosts
- **services** info su services

ora possiamo utilizzare direttamente metasploit come se fosse nmap e ci memorizzerà ed aggiornerà ciò che troviamo con le scan

ES: **db_nmap nmap -T4 -sA -A -vvv -p- -Pn** **IP_TARGET**

