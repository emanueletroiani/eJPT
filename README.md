### Privilege Escalation

è il processo di sfruttamento di vulnerabilità o configurazioni errate nei sistemi per **elevare** i **privilegi da un utente a un altro**, tipicamente a un utente con accesso amministrativo o root su un sistema.

- L'elevazione dei privilegi **è un elemento cruciale** del ciclo di vita di un attacco e un fattore determinante per il successo complessivo di un test di penetrazione.
- Dopo aver ottenuto un primo **punto d'appoggio** **su un sistema target**, sarà necessario **elevare** i propri privilegi **per eseguire** attività e funzionalità che richiedono **diritti amministrativi.**
- L'importanza dell'elevazione dei privilegi nel processo di penetration testing non può essere sopravvalutata o trascurata. **Sviluppare competenze in questo ambito ti distinguerà come un esperto tester di penetrazione.**

### Windows Kernel

**Il Kernel** è un programma informatico che costituisce il **nucleo** di un **sistema operativo** e ha il **controllo** completo su ogni **risorsa** e **hardware** del **sistema**. Funge da **strato** di **traduzione tra** **hardware e software**, facilitando la comunicazione tra questi due livelli.

- **Windows NT** **è il kernel preinstallato** in tutte le versioni di Microsoft Windows e opera come un kernel tradizionale, con alcune eccezioni basate sulla filosofia di progettazione utente. È composto da due modalità operative principali che determinano l’accesso a risorse di sistema e hardware:
    - **Modalità utente** – I programmi e i servizi in esecuzione in questa modalità hanno accesso limitato alle risorse e alle funzionalità del sistema.
    - **Modalità kernel** – La modalità kernel ha accesso illimitato alle risorse e alle funzionalità del sistema, inclusa la gestione dei dispositivi e della memoria di sistema.

### Exploit del Kernel Windows

- Gli exploit del kernel su Windows puntano solitamente a vulnerabilità nel kernel di Windows per eseguire codice arbitrario, con l’obiettivo di eseguire comandi di sistema privilegiati o ottenere una shell di sistema.
- Questo processo varia in base alla versione di Windows target e all’exploit del kernel utilizzato.
- **L’elevazione dei privilegi** sui sistemi Windows segue tipicamente questa metodologia:
    - **Identificare le vulnerabilità del kernel.**
    - **Scaricare, compilare e trasferire gli exploit del kernel sul sistema target.**

### EXPLOIT

METASPLOIT

1. **getsystem** comando che aumenta i privilegi automaticamente con diverse tecniche, se fallisce procediamo oltre
2. **search suggester**
3. **use post/multi/racon/local_exploit_suggester** modulo che elenca tutte le vulnerabilità con i relativi exploit da sfruttare per un privilege escalation, funziona su **tutti** i **sistemi operativi**
    1. **set SESSION** essendo un modulo di post exploitation bisogna dargli una sessione su cui partire (sulla spiegazione mette una sessione meterpreter)
    2. **run**

MANUALE

il metodo manuale permette di ottenere piu possibili vulnerabilità  per aumentare i privilegi, non è rilevabile dai sistemi di sicurezza ma è complicato da utilizzare. Di seguito i tool con le guide

- **Windows-Exploit-Suggester** – Questo strumento **confronta** il livello di **patch** **del target** **con** il database delle **vulnerabilità Microsoft** per **rilevare** potenziali **patch mancanti**. Inoltre, segnala se sono disponibili exploit pubblici o moduli Metasploit per i bollettini mancanti.
    - GitHub: https://github.com/AonCyberLabs/Windows-Exploit-Suggester da notare che le vulnerabilità verranno elencate dalla piu efficace alla meno
- **Windows-Kernel-Exploits** – Raccolta di exploit per il kernel Windows organizzati per CVE.
    - GitHub: https://github.com/SecWiki/windows-kernel-exploits/tree/master/MS16-135
