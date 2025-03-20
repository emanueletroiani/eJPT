### Cosa sono i Token di accesso Windows

Sono un **elemento** fondamentale per il **processo** di **autentificazione** in **Windows**, vengono **creati** e **gestiti** dal **LSASS** (Local Security Authority Subsystem Service).

**Permette** ad un **utente** di **accedere** ad un **sistema** o una **risorsa senza** dover **fornire** le **credenziali** **ogni** qual **volta.**

Quando un **utente utilizza** un **token** esso **viene associato** ad un **Thread** o al processo, i token di accesso vengono **generati** da **winlogon.exe**

**Esempio**: Se noi **avviamo** un **processo** e **generiamo** un **token**, esso **ogni volta che creerà un processo figlio** **non** dovrà **chiedere l’autorizzazione all’utente** ma **utilizzerà** lo stesso **token** generato dal processo padre.

Vengono **suddivisi** in **livelli** di sicurezza e ad **ogni livello** di sicurezza ha **determinati privilegi.**

- **Livello impersonato:** vengono **creati** come **risultato** **diretto** di un **login non interattivo** su windows, in genere attraverso servizi di sistema specifici
- **Livello delegato**: vengono **creati** attraverso **login interattiv**o su windows, come **login** **tradizionali** o attraverso protocolli come **RDP**

I token di livello Impersonato possono essere utilizzati per impersonare un token sul sistema locale e non sistemi esterni che utilizzano il token.

I token a livello di **delegato** rappresentano la **minaccia maggiore**, in quanto possono essere **utilizzati** per **impersonare** i **token** su **qualsiasi sistema.**

### COME SFRUTTARE I TOKEN PER AUMENTARE I PRIVILEGI

Per i Token impersonati dipende dai privilegi che ha l’utente che abbiamo exploitato.

Di seguito sono riportati i privilegi necessari per la riuscita di un attacco di impersonificazione:

- **SeAssignPrimaryToken:** Consente a un utente di impersonare i token.
- **SeCreateToken:** Consente a un utente di creare un token arbitrario con privilegi
- **SeImpersonatePrivilege:** Consente a un utente di creare un processo sotto il contesto di sicurezza di un altro utente, in genere con privilegi amministrativi.

### IL MODULO INCOGNITO

Consente di impersonare i token degli utenti dopo uno sfruttamento

Possiamo usare il modulo incognito per visualizzare un **elenco** di **token disponibili che possiamo impersonare.**

1. Porta http aperta, check ip browser per vedere se c’è servizio HFS
2. **use exploit/windows/http/rejetto_hfs_exec**
3. **sysinfo**
4. **getuid**
5. **getprivs** vediamo se c’è uno dei privilegi necessari per sfruttare vulnerabilità Token
6. **load incognito** carichiamo il modulo incognito (stamperà a schermo una conferma del caricamento
7. **list_tokens -u** stampa lista token Delegation e Impersonation
8. **copiamo il nome dell’utente** su cui vogliamo impersonificarci ES: **ATTACKDEFENSE\\Administrator** 
9. **impersonate_token ATTACKDEFENSE\\Administrator** aumeta i privilegi.
10. **getprivs** se non funziona:
    1. **pgrep explorer** trova l’ID del processo explorer.exe
    2. **migrate ID_EXPLORER.EXE**
