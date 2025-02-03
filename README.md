Samba è il **protocollo** utilizzato per **condividere** i **file** tra host in una rete **locale.** Di default utilizza porta **445 TCP** sui nuovi dispositivi Windows porta **139 NETBios**

Samba è stato implementato da Linux per permettere ai sistemi windows di accedere alle cartelle e dispositivi.

Permette anche agli **utenti** di **connettersi** alle **stampanti**

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **search portscan**
5. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
6. **search type:auxiliary name:smb** permette la ricerca del tipo di modulo e il nome da cercare
7. **auxiliary/scanner/smb/smb_version** enumerzione versione servizio smb
8. **scanner/smb/smb_enumshares** per enumerazione cartelle
9. **auxiliary/scanner/smb/smb_login** bruteforce per entrare in un account
    1. **set SMBUser admin** utilizziamo sempre l’utente admin
    2. **set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt**
    3. **set STOP_ON_SUCCESS true**
