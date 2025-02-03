Il **protocollo SSH (Secure Shell)** è un protocollo di rete crittografato utilizzato per stabilire una **connessione** sicura **tra due** **macchine**, tipicamente un client e un server. **SSH** fornisce un **metodo sicuro** per **accedere** e **gestire** **sistemi remoti** attraverso una rete non sicura, come Internet, consentendo **l’esecuzione** di **comandi**, il **trasferimento** di **file**, il **tunneling** e altro, proteggendo la riservatezza e l'integrità dei dati tramite crittografia.

Di default utilizza la **porta 22**

### ENUMERAZIONE SSH

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **setg RHOST IP_TARGET** memorizza il target ip nei moduli
5. **setg RHOSTS IP_TARGET** memorizza il target ip nei moduli
6. **search portscan**
7. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
8. **search type:auxiliary name:ssh**permette la ricerca del tipo di modulo e il nome da cercare
9. **auxiliary/scanner/ssh/ssh_version** trova versione servizio
10. **auxiliary/scanner/ssh/ssh_enumusers** trova utenti
    1. **USER_FILE**  /usr/share/metasploit-framework/data/wordlists/common_users.txt
11. **auxiliary/scanner/ssh/ssh_login** modulo per bruteforce
    1. **PASS_FILE** /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **oppure** /usr/share/metasploit-framework/data/wordlists/common_passwords.txt
    2. **USER_FILE**  /usr/share/metasploit-framework/data/wordlists/common_users.txt
    3. **sessions** per vedere se abbiamo una sessione interattiva con una shell
    4. **sessions NUMERO_SESSIONE** per accedere alla sessione con una shell
    5. **/bin/bash -i** crea una shell interattiva  (non sempre funge)
