Un **Web server** è un **software** che viene utilizzato per servire i dati di un sito web nella rete web.

**Utilizza** il protocollo **HTTP** per facilitare le comunicazioni tra clients e web server.

**Famosi** Web server sono **Apache**, **Nginx** e **Microsoft IIS**

### Qual’è il processo di apertura di una pagina web

1. digitiamo il sito HTTP/HTTPS nel browser
2. Il DNS risolverà il nome del dominio in un IP con una ricerca nelle sue tabelle di IP
3. il server web invierà una richiesta HTTP di risposta al Browser contenente generalmente info come dati del sito web

### ENUMERAZIONE HTTP

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **setg RHOST IP_TARGET** memorizza il target ip nei moduli
5. **setg RHOSTS IP_TARGET** memorizza il target ip nei moduli
6. **search portscan**
7. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
8. **search type:auxiliary name:http** permette la ricerca del tipo di modulo e il nome da cercare
9. **auxiliary/scanner/http/http_version** trova versione servizio (su target HTTPS cambiare porta con 443 o 139 e mettere SSL true) 
10. **auxiliary/scanner/http/http_header** versione http, tipo di programma di linguaggio con è sviluppato il sitoweb ospitato nel webserver, data ultima modifica e numero Header
11. **auxiliary/scanner/http/robots_txt** cerca directory volutamente nascoste
    1. per ottenere info se troviamo cartelle non protette da password utilizziamo **curl IP_TARGET/DIRECTORY/**
12. **auxiliary/scanner/http/dir_scanner** enumera con bruteforce le directory
    1. per ottenere info se troviamo cartelle non protette da password utilizziamo **curl IP_TARGET/DIRECTORY/**
13. **auxiliary/scanner/http/files_dir** enumera i file all’interno delle direcotry
14. **auxiliary/scanner/http/http_login** Brute force per accedere a cartelle protette da passwword
    1. **set AUTH_URI** mette percorso directory da enumerare
    2. **PASS_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
    3. **USER_FILE** metasploit default /usr/share/metasploit-framework/data/wordlists/common_users.txt



