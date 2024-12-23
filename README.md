Tutto su [Iso/Osi](https://github.com/emanueletroiani/I-miei-studi/blob/I-Livelli/README.md)

![Screenshot 2024-12-21 122102](https://github.com/user-attachments/assets/531fd47d-8a82-4b8e-9579-98c0d6739f1b)

# Network Layer

La sua funzione principale è quella di mettere in comunicazione attraverso gli IP e il percorso migliore i dispositivi. qui si parla degli indirizzi IP, spiegati qui (linkare spiegazioni IP

- **MTU** **protocol** è il protocollo che permette di frammentare i pacchetti di grosse dimensioni che attraversano la rete e di assemblare i frammenti piccoli ricevuti nel pacchetto originale

![image](https://github.com/user-attachments/assets/f1f05fac-5a0e-4dd0-b38f-6db69168d3a3)

## eader IPv4

- **IP Source Address:** Emittente del pacchetto
- **IP Destination Address:** Destinazione del pacchetto
- **Time To Live**: un valore di 8 bit che indica il tempo di vita di un pacchetto
- **Type of Service (ToS)**: Contiene un valore binario di 8bit che determina la priorità dei pacchetti (flow control, congestione pacchetti)
- **protocol**: è un valore di 8 bit che indica il tipo di dati del payload che il pacchetto porta

## IPv4 Header Fields

- **Version**: la versione dell’IP (4 o 6)
- **Identification**: usato per il riasseblamento dei pacchetti frammentati. Ad ogni frammento di un pacchetto venne assegnato lo stesso valore identificativo
- Flags: Ci posso essere 3 flags
    - **Bit 0**: impostato sempre a zero
    - **DF, bit 1**: se impostato ad 1 indica che i pacchetti non devono essere riassemblati
    - **MF, bit 2**: se impostato ad 1 indica che piu pacchetti fanno parte di un pacchetto frammentato
- **TTL**: rappresenta il massimo numero di Hops all’interno di un router he il pacchetto può’ attraversare prima che venga scartato. Ogni Hop che fa il numero decresce
- **Protocollo**: sono segnati a numero. 6 per TCP, 17 per UDP, 1 per ICMP

TUTTO SULL’[IP](https://github.com/emanueletroiani/I-miei-studi/blob/IP-Internet-Protocol/README.md)

# Trasport layer

## COME SONO I IMPOSTATI I FLAGS DELL’HEADER DI UN PACCHETTO TCP

![image](https://github.com/user-attachments/assets/c6753f00-10c5-4cda-8317-cd55be1f2d23)

![image](https://github.com/user-attachments/assets/9085d669-b6a9-4feb-9c35-4cbdc6fd3052)

NETSTAT

- **netstat -antp** permette di vedere le connessioni TCP attuali dell’host

# Network Mapping

## CHE COS’E’

Dopo aver ottenuto informazioni del target dopo la **Passive information gathering**, solitamente un Penetration Test si muove nella direzione dell’ **Active information Gathering** per scoprire host nella rete, le porte aperte e enumerare. Il **network mapping** è ciò che ci fa determinare se un Host è online, quali porte sono aperte e quali servizi sono avviati sulle porte

Per un **Pentester** è **essenziale** per i primi passi di una raccolta di informazioni, come la **disposizione della rete**, **capire l’architettura** e **identificare punti di accesso per** un eventuale futuro **exploit**

## PERCHE’ CI SERVE MAPPARE UNA RETE

Mettiamo caso siamo stati ingaggiati da una compagnia che ha un indirizzo di rete 200.200.0.0/16 ovvero dispone di 65536 IP con una subnet di 200.200.255.255. Il primo Lavoro che deve fare un PT è quello di capire quali IP sono stati assegnati all’host e quali sono online/attivi

## L’IMPORTANZA DI CREARE UNA MAPPA DELLA RETE TARGET

Creare una mappa o un diagramma della topologia della rete ci farà capire la disposizione della rete per pianificare un fare futura di penetration testing attivo. La mappa deve contenere **router, switches, firewalls e altri elementi infrastrutturali di rete.**
