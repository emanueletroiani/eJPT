- Meterpreter (Meta-Interpreter) è un **payload** multifunzionale **avanzato** che
**opera tramite** l'**iniezione di DLL** e viene **eseguito in memoria** sul sistema di
destinazione, rendendo così **difficile** il suo **rilevamento**.
- Comunica attraverso un **socket stager** e fornisce all'aggressore un interprete di comandi
interattivo sul sistema di destinazione che facilita l'esecuzione di comandi di sistema, la
navigazione nel file system, il keylogging e molto altro.
- Meterpreter ci permette anche di **caricare** dinamicamente **script** e **plugin** **personalizzati**.
- MSF fornisce **vari** tipi di **payload meterpreter** che possono essere utilizzati **in base**
**all'ambiente** di destinazione e **all'architettura** del sistema operativo.

COMANDI DA UTILIZZARE 

1. `sysinfo`
2. `getuid`
3. `help` Lista i comandi
4. `pwd`
5. `cat`
6. `edit` apre un editor di testo per modificare il file selezionato
7. `cd “DIRECTORY”` naviga nella directory, gli apici aprono piu direcotory rispetto a /
8. `download` scaricare file 
9. `search -d DIRECTORY -f *FILE*` cerca il nome del file all’interno della directory 
    1. -**d** directory dove cercare
    2. **-f** nome del file da cercare
        1. ES: `search -f *.txt`
10. `shell`
    1. `/bin/bash -i` crea una shell classica linux
11. `sessions -h` lista i comandi che possiamo utilizzare per interagire con le sessioni meterpreter ottenute
12. `sessions -C sysinfo -i 1` invia il comando sysinfo sulla sessione numero 1
    1. **-C** invia un comando meterpreter sulla sessione -i
    2. **-i** INteragisce con quella sessione
13. `sessions -n NAME -i N_SESSIONE` da un nome alle sessione N
