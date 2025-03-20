- `sudo apt-get update && sudo apt-get install exploitdb -y` **integrare exploit-db** nel tool **searchsploit**
1. `searchsploit -u` per fare l’update (fare tutti i giorni)
2. `searchsploit -t PAROLA` cerca la parola nel titolo dell’ exploit
3. `searchsploit TIPO PIATTAFORMA SERVIZIO` ricerca specifica
    1. **TIPO**: remote, dos, local (tag per privilege escalatio), webapps
    2. **PIATTAFORMA**: Android, Java, IOS, Linux, Windows, macos etc etc (andare sul sito e vedere dai filtri)
    3. **SERVIZIO**: ssh, mysql, ftp, http, buffer, wordpress etc etc
        1. ESEMPIO1 `searchsploit remote linux ssh`
        2. ESEMPIO2 `searchsploit remote webapps wordpress` 
        3. ESEMPIO3 `searchsploit local windows | -e grep " Microsoft"` local è il tag per il **privilege escalation**
4. `sudo cp /usr/share/exploitdb/exploits/PATH_EXPLIOIT .` per copiare nella directory attuale l’exploit

4. `searchsploit -m /PATH` per copiare nella directory attuale l’exploit
