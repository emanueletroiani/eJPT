# Tecniche

- **Ping Sweeps (ICMP Echo Requests)**: metodo piu utilizzato e veloce che consiste nel **mandare un ping** ad uno o piu IP per identificare se l’host è attivo.
- **ARP Scanning:** Utilizzato per identificare gli Host all’interno di un local network. Funziona mandando un ARP Broadcast.
- **TCP SYN Ping (HALF-Open Scan)**: Sfruttano solitamente la porta 80 per mandare pacchetti TCP SYN, se l’host è attivo risponderà con un TCP SIN-ACK. E’ una tecnica **stealth.**
- **UDP Ping:** Utilizzato quando l’host target non risponde a ICMP e TCP. Manda pacchetti UDP ad una specifica porta per verificare se l’host è online.
- **TCP ACK Ping**: Questa tecnica manda un pacchetto TCP ACK  ad una porta specifica per vedere se è online. Non riceve alcuna risposta ma se il **TCP RST** è stato ricevuto allora l’host è online
- **SYN-ACK Ping:** Manda pacchetti TCP SYN-ACK ad una porta specifica, se si riceve una risposta TCP RST l’host è attivo

# Quale tecnica scelgo?

Dipende da tanti fattori:

- ICMP Ping:
    - **Pro**: è ampiamente supportato e un metodo veloce.
    - **Contro**: alcuni Hosts e Firewalls possono essere configurati per bloccare o limitare le richieste di Ping. E’ facilmente rilevabile.
- TCP SYN Ping:
    - **Pros**: E’ stealth e a volte può bypassare i firewalls
    - **Cons**: Alcuni Hosts possono non rispondere a richieste TCP SYN, e i risultati possono essere effettuati da Firewalls o dispositivi di sicurezza.

# Ping Sweeps

E’ un tecnica per scannerizzare una rete che serve per **trovare l’IPs Hosts** **all’interno** di un in uno specifico range di una rete. Funziona semplicemente mandando una serie di Ping in un range di IP e se si ottengono risposte determina che Host è attivo.

Se **l’host** di destinazione **risponde** con un **pacchetto ICMP** (type 0) allora l’ **host** è **attivo**. I messaggi che vediamo quando pinghiamo un IP si chiamano **Echo Request** e **Echo Replay**. Questi messaggi hanno tipi specifici di ICMP e dei valori di codice associati con loro

- ICMP Echo Request
    - Type 8
    - Code 0
- ICMP Echo Reply
    - Type 0
    - Code 0

# Comandi Ping

Kali 

- **ping -c N° IP_TARGET** indica quanti pacchetti inviare al target

Windows

- **ping -n N° IP_TARGET** indica quanti pacchetti inviare al target

---

- **ping -b -c N° IP_RETE** manda pacchetto ad ogni host sulla rete target es: ping  -b -c 1 192.168.1.0
- **fping -a -g IP_RETE/SUBNET** pingare tutti gli host sulla rete ES fping -a -g 192.168.1.0/24
- **fping -a -g IP_RETE/SUBNET 2>/dev/null**  per eliminare l’elenco di ping agli IP offline

