### **SMB**

- SMB è un protocollo di condivisione file in rete.
- Usa la porta TCP 445 o 139 NETBios
- **SAMBA** è l'implementazione open source di SMB **per Linux.**

### **Autenticazione SMB**

- SMB utilizza 2 livelli di autenticazione:
    - autenticazione utente
    - autenticazione condivisione.
- Entrambi i livelli utilizzano un sistema di autenticazione username e password

![image](https://github.com/user-attachments/assets/d9810dc9-2ea1-4e36-82c3-cf573cfc5289)

### **PsExec**

- PsExec è un'utility leggera sviluppata da Microsoft per eseguire processi su sistemi Windows che sostituisce Telnet
- Possiamo autenticarci tramite SMB per poi eseguire comandi arbitrari o lanciare un comando remoto
- Simile a RDP, ma invece di controllare il sistema remoto tramite GUI, i comandi vengono inviati tramite CMD.

### **Sfruttamento di SMB con PsExec**

- Per utilizzare PsExec, è necessario identificare account utente legittimi e le relative password o hash.
- Si può eseguire un attacco brute-force su SMB per ottenere credenziali.
- Dopo aver ottenuto le credenziali, si può autenticare sul sistema target ed eseguire comandi arbitrari.

### exploit

- **auxiliary/scanner/smb/smb_login** bruteforce per entrare in un account
    1. **set SMBUser admin** utilizziamo sempre l’utente admin
    2. **set PASS_FILE /**usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **oppure** /usr/share/metasploit-framework/data/wordlists/common_passwords.txt
    3. **set STOP_ON_SUCCESS true**
- **use exploit/windows/smb/psexec**  permette di ottenere shell
    - set RHOSTS
    - set SMBUser
    - set SMBPass
