**Servizi Windows frequentemente sfruttati**

- Windows ha vari servizi nativi che possono essere configurati per essere eseguiti su un host.
- Questi servizi forniscono un vettore di accesso per gli attaccanti.
- È importante comprendere questi servizi, come funzionano e le loro potenziali vulnerabilità.

| **Protocollo/Servizio** | **Porte** | **Scopo** |
| --- | --- | --- |
| Microsoft IIS (Internet Information Services) | TCP 80/443 | Software pubblicato da Microsoft che **trasforma** il **computer** su cui è in esecuzione in un **server web** |
| WebDAV (Web Distributed Authoring & Versioning) | TCP 80/443 | Estensione **HTTP** che permette di **aggiornare**, **cancellare**, **spostare** e **copiare** **file** su un **server web.** |
| SMB/CIFS (Server Message Block Protocol) | TCP 445 | Protocollo di condivisione file in rete. |
| RDP (Remote Desktop Protocol) | TCP 3389 | Protocollo di accesso remoto GUI sviluppato da Microsoft. |
| WinRM (Windows Remote Management Protocol) | TCP 5986/443 | Protocollo di gestione remota di Windows. |

