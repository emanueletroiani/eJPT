![Screenshot 2024-12-21 105438](https://github.com/user-attachments/assets/8f7b7403-f457-4a31-8658-0f52da0e1975)

# Passive

Cosa cerchiamo:

- IP Addresses
- Directories nascoste dai motori di ricerca
- Nomi
- Email
- Numeri di Cellulare
- Indirizzi Fisici
- Tecnologie web utilizzate

# Active Da kali

- **host DOMAIN_NAME**
- **dirb DOMAIN_NAME**
- **dirb DOMAIN_NAME -w /usr/share/dirb/wordlists/common.txt -X FILE_EXSTENSION** trova file all’interno delle directory del target IP
- **dnsrecon -d DOMAIN_NAME** trovare record dns
- **sublist3r -d DOMAIN_NAME**
- **sublist3r -d DOMAIN_NAME -e google,yahoo**
    - -**d**: ricerca i sottodomini
    - -**e**: utilizza i motori di ricerca selezionati
    - Con una VPN sorpassa i blocchi

Questo tool ci permette di individuare i possibili WAF che proteggono il sito.

- **wafw00f DOMAIN_NAME**
- **wafw00f DOMAIN_NAME -a** cerca tutti i possibili WAF
- **theHarvester -d DOMAIN_NAME -l 100 -b FONTE,ALTRA FONTE** (fonti ma mettere su si trovano [qui](https://github.com/laramies/theHarvester) sotto la voce passive)
    - -**d** target dominio
    - -**l** (L minuscola) massimo 100 risultati
    - **-b** fonte da cui prendere i dati
- **fierce -dns DOMAIN_NAME** zone transfert come è articolata una rete
- **ip a** ip su eth0 è il nostro. se mettiamo la rete su nmap possiamo vedere gli indirizzi connessi.
    - ES:
    - **eth0 10.0.2.15/24**
    - **sudo nmap -sn 10.0.2.0/24** per vedere host connessi
- **sudo netdiscover -i eth0 -r IP_INDIRIZZO_RETE** per sapere tutti i dispositivi collegati sulla rete
- **nmap -A -sV --open -O -Pn -sC -vv IP > nmapscan.txt**

# Da Url

- **DOMAIN_NAME/robots.txt** directory nascoste
- Per trovare [sottodomini](https://www.netcraft.com/?utm_feeditemid=&utm_device=c&utm_term=netcraft&utm_source=google&utm_medium=ppc&utm_campaign=Google+%7C+Search+%7C+Brand+%7C+Exact+%7C+20221014&hsa_cam=18600605269&hsa_grp=150893442948&hsa_mt=e&hsa_src=g&hsa_ad=689927749890&hsa_acc=4527524350&hsa_net=adwords&hsa_kw=netcraft&hsa_tgt=kwd-514047884592&hsa_ver=3&gad_source=1&gclid=EAIaIQobChMIzILh18G2igMVEwcGAB2zCANbEAAYASAAEgL45vD_BwE)

# Dorks

- **site:WEB_DOMAIN inurl:admin** per cercare all’interno del sito web o all’interno dell’URL se c’è una pagine da Amministratore
- **site:*.WEB_DOMAIN** enumerare i sottodomini
- **site:*.WEB_DOMAIN**  **inurl:admin** sottodominio da Amministratore
- **site:*.WEB_DOMAIN**  **intitle:admin** sottodominio da Amministratore contenuti nel titolo
- **site:*.WEB_DOMAIN**  **filetype:pdf** all’interno dei sottodominio cerca file pdf
- **site:*.WEB_DOMAIN**  **filetype:xlsx** all’interno dei sottodominio cerca file xlsx
- **site:*.WEB_DOMAIN**  **filetype:doc**
- **site:*.WEB_DOMAIN**  **filetype:zip**
- **site:*.WEB_DOMAIN**  **filetype:jpg**

Ricerche sui dipendeti

- **site:WEB_DOMAIN employees**
- **site:WEB_DOMAIN** **instructors**

Vedere Directory

- **site:WEB_DOMAIN intitle:index of** mostra le directory (se vulnerabile)

Vedere il sito come era giorni o mesi prima

- **waybackmachine** sito web che lo permette

Directory con password

- **inurl:auth_user_file.txt**
- **inurl:password.txt**
- **intitle:password.txt**

# BEST SITO PER DORKS

https://www.exploit-db.com/google-hacking-database

- **file containing passwords** è un filtro che mostra dorks per la ricerca di pass
- **wp** in quick search mostra dorks di wordpress
