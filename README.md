FTP (File Transfer Protocol) è un protocollo che utilizza la porta TCP 21 ed è usato per facilitare la condivisione di file tra un server e un cliente.

- Utilizzato anche per trasferire file da e verso le directory di un server Web
- Servizio che necessita credenziali
- Consente Anonymous login se configurati per questo

- **hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt IP_TARGET -t 4 ftp**
    - **-t 4** thread che impostiamo in quanto può causare un crash del sistema

CON METASPLOIT

1. **auxiliary/scanner/ftp/anonymous** modulo per verificare se è presente vulnerabilità Anonymous 
2. **auxiliary/scanner/ftp/ftp_login** modulo per bruteforce
    1. **BRUTEFORCE_SPEED**
    2. **PASS_FILE** /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt **oppure** /usr/share/metasploit-framework/data/wordlists/common_passwords.txt
    3. **USER_FILE** /usr/share/metasploit-framework/data/wordlists/common_users.txt
- **ftp USERNAME@IP_TARGET** per accedere al protocollo ftp
