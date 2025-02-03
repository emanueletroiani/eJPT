MySQL è un **database relazionale** open source di **gestione** basato su **linguaggio SQL**

Viene utilizzato per **memorizzare** i **dati** delle applicazioni web, esse contengono anche dati dei clienti come pass ed username.

Utilizza la **porta 3306** di default.

### ENUMERAZIONE mySQL

pass esercizio root:twinkle

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **setg RHOST IP_TARGET** memorizza il target ip nei moduli
5. **setg RHOSTS IP_TARGET** memorizza il target ip nei moduli
6. **search portscan**
7. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
8. **search type:auxiliary name:sql** permette la ricerca del tipo di modulo e il nome da cercare
9. **auxiliary/scanner/mysql/mysql_version** trova versione servizio da exploitare
10. **auxiliary/scanner/mysql/mysql_login** esegue un bruteforce per il login al server del database mysql
    1. **PASS_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
    2. **USER_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/common_users.txt
11. **auxiliary/admin/mysql/mysql_enum**  permette di enumerare in modo semplice il server di database MySQL a condizione che siano fornite le credenziali adeguate. Alcune INFO che trova:
    1. MySQL version
    2. Sistema oprativo
    3. Server name
    4. percorso Data Directory
    5. Se è presente una connessione SSL
    6. **Enumerazione degli account** trova nome username in chiaro e l’hash delle password che possono essere decriptate con le rainbow table
12. **auxiliary/admin/mysql/mysql_sql** permette di eseguire una query sql sul database mysql tramite **credenziali di accesso**
    1. **set SQL** ecco alcune opzioni
        1. **set SQL show databases**; mostra i database 
        2. **set SQL use NOME_DATABASE_TROVATO;** entra dentro al database selezionato
13. **auxiliary/scanner/mysql/mysql_schemadump** mostra lo schema della struttura del database
