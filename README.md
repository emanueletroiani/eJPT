Utilizza la **porta 21**, il suo compito è di facilitare il trasferimento di file tra server e client to clients.

Utilizzato anche per il **trasferimento** di file **da** e **tra** le **directory** di un **web** server

Per enumerarlo ci sono diversi auxiliary come i bruteforce in quanto utilizza delle credenziali di accesso vulnerabile anche ad anoniymous

# Esempi enumerazione FTP

### Vulnerabilità versione servizio

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **search portscan**
5. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
6. **search type:auxiliary name:ftp** permette la ricerca del tipo di modulo e il nome da cercare
7. **auxiliary/scanner/ftp/ftp_version** ci permette di trovare la versione del servizio
8. settare tutte le options
9. exploit per ottenere versione servizi
10. trovato l’xploit per la versione abbiamo Finita la fase di enumerazione. 

### Brute force per FTP

1. **search type:auxiliary name:ftp** permette la ricerca del tipo di modulo e il nome da cercare
2. **auxiliary/scanner/ftp/ftp_login** modulo per bruteforce
3. settare le options
    1. **BRUTEFORCE_SPEED**
    2. **PASS_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
    3. **USER_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/common_users.txt
4. ftp TARGET

### Anonymous vulnerabilità check

1. **search type:auxiliary name:ftp** permette la ricerca del tipo di modulo e il nome da cercare
2. **auxiliary/scanner/ftp/anonymous** modulo per verificare se è presente vulnerabilità anonymous
