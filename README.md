La **scansione** e il **rilevamento** delle **vulnerabilità** è il processo di scansione di un obiettivo alla ricerca di vulnerabilità e **verificare se possono** essere **sfruttate**.

1. cerchiamo porte aperte
2. troviamo la versione dei servizi sulle porte aperte

### CON METASPLOIT

1. cerchiamo il nome della versione per vedere se c’è un exploit
    1. **search NOME_VERSIONE**
    2. **search type:exploit name:SERVIZIO**
2. trovato l’exploit utilizziamolo
3. **info** per vedere se l’exploit va bene per la versione del servizio
4. cerchiamo il payload per il sistema operativo giusto e quello che fa al caso nostro
    1. **search peyload**
5. ci fermiamo qui per il momento

### SU SHELL

1. **searchsploit “NOME_SERVIZIO”** cerca exploit per quel servizio
2. **searchsploit “NOME_SERVIZIO” | grep -e “Metaploit”** cerca solo i moduli per metasploit

### Plug-in [autopwn](https://github.com/hahwul/metasploit-autopwn)

Scaricabile su kali tramite github repository

Autopwn individua moduli metasploit di porte aperte sul sistema target

**Come impostarlo**

1.  **wget https://raw.githubusercontent.com/hahwul/metasploit-autopwn/master/db_autopwn.rb**
2. ora bisogna spostare il database nella share metasploit
    1. **cd metasploit-autopwn**
    2. **cp db_autopwn.rb /usr/share/metasploit-framework/plugins**
3. su MSF **load db_autopwn**
4. **db_autopwn -p -t -PI**
    1. **-p** seleziona i moduli in base alle porte aperte
    2. **-t** mostra tutti i moduli degli exploit metchati
    3. **-PI N°_PORTA** specifica quali exploit trovare sulla porta target aperta dell’hos
    
5. **analyze** analizza tutto cio’ che abbiamo trovato sull’ host target e mostra quali exploit possono essere sfruttate.
6. **vulns** mostra le vulnerabilita’ trovate


