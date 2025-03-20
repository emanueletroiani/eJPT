### EMPIRE

E’ un framework di puro sfruttamento/post sfruttamento costruito su comunicazioni sicure dal punto di vista crittografico.

Utilizza agenti PowerShell senza bisogno di powershell.exe, moduli post-exploitation rapidamente distribuibili che vanno dai keylogger a Mimikatz e comunicazioni adattabili per eludere il rilevamento

https://www.kali.org/blog/empire-starkiller/

### Starkiller

Starkiller è un'interfaccia grafica per Powershell Empire. 

https://www.powershellempire.com/

---

- **Listeners** sono i dispositivi in ascolto
- **agents** sono i dispositivi exploitati (di cui hai accesso)
1. `sudo apt-get update && sudo apt-get install powershell-empire startkiller -y` installa Empire
2. `sudo powershell-empire server` avviamo il server di empire

NEW TAB

1. `sudo powershell-empire client` su una nuovo CLI apriamo il client
2. avviare il tool `starkiller`
    1. **username** empireadmin
    2. **password** password123
3. creare un `listner`
    1. **http** o **http_hop** sono i consigliati
    2. **host** mettiamo il nostro IP
    3. **port** una delle porte in opzione
    4. **Headers** se vogliamo possiamo modificarlo
    5. **create**
4. creare uno `stager` (vittima)
    1. **windows/csharp_exe** 
    2. **listern** selezioniamo quello creato in precedenza
    3. **outfile** sarebbe il nome dello stager una volta creato
    4. **offuscation** offusca il codice, serve per evadere gli AV
    5. **create**
    6. **download**
5. ora bisogna caricare ed avviare sul target lo stager e riceveremo la connessione su starkiller
