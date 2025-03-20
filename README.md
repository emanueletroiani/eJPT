- Tutte le **informazioni** per tutti gli **account** su Linux sono memorizzate nel file passwd che si trova in: **/etc/passwd**
    - Non è possibile visualizzare le **password** degli utenti nel file passwd perché sono **criptate** e il file passwd è leggibile da qualsiasi utente del sistema.
- Tutte le **password crittografate** degli utenti sono **memorizzate** nel file shadow, che si trova nella
seguente directory: **/etc/shadow**
    - Il file shadow è **accessibile e leggibile solo dall'account root**
- **Il file passwd fornisce informazioni sull algoritmo di hashing**

Valore Algoritmo di hashing
**$1 - MD5
$2 - Blowfish
$5 - SHA-256
$6 - SHA-512**

DUMB PROCESS

-MANUALE

1. cat /etc/shadow
2. Decodificare in base all’algoritmo utilizzato

-AUTOMATICO CON METASPLOIT

1. Bisogna **avere** una **sessione meterpreter** sul target
2. **use /post/linux/gather/hashdump**
    1. **set SESSION**
