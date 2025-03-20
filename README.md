- **Oltre ai tre principali permessi** di accesso ai file (lettura, scrittura ed esecuzione), **Linux** fornisce
agli utenti anche **permessi** speciali che possono essere **utilizzati** in **situazioni specifiche**. **Uno** di
questi permessi di accesso **è il permesso SUID** (Set Owner User ID).
- **Consente** agli utenti di **eseguire** uno **script** o un file **binario con i permessi del proprietario** del file e **non dell'utente che sta eseguendo lo script** o il file binario.
- I permessi SUID sono tipicamente **utilizzati** per **fornire** agli **utenti non privilegiati** la **possibilità** di
**eseguire script** o file binari specifici **con** i permessi di "**root**". Va notato, **tuttavia**, che la fornitura di **privilegi** **elevati** è **limitata all'esecuzione dello scrip**t e non si traduce in un'elevazione dei privilegi, **ma** gli utenti non privilegiati possono **sfruttare** **configurazioni errate** o vulnerabilità all'interno del binario o dello script **per ottenere una privilege escalation**
- il **successo** del nostro attacco **dipenderà** dai **seguenti fattori**:
    - **Proprietario del binario SUID** - Dato che stiamo cercando di elevare i nostri
    privilegi, sfrutteremo solo i **binari SUID** di **proprietà** dell utente "**root**" o di altri
    utenti privilegiati.
    - **Permessi di accesso** - Per eseguire **il binario SUID** sono **necessari** i **permessi** di
    **esecuzione**.

```
ls -l
```

![](https://assets.ine.com/lab/learningpath/9e5a8b1863914db7c99ef77be50e0a887290cb170b1ec63fa5ce929d4a916f4e.jpg)

**Step 5:** Observe that the welcome binary has suid bit set (or on). This means that this binary and its child processes will run with root privileges. Check the file type.

**Command:**

```
file welcome
```

![](https://assets.ine.com/lab/learningpath/4cd4d0c3553deee844022f798e7a22a6352eb2979287aa9ea89ac89c8eca3c18.jpg)

It is an ELF binary. And on execution, it shows a welcome message.

![](https://assets.ine.com/lab/learningpath/b092892db3f93122360f1976d543e1756fe8e6dce68f95f2ddd3c22de95b6fa2.jpg)

**Step 6:** Investigate the binary. The most easy or preliminary way of doing that is to use strings command.

**Command:**

```
strings welcome
```

![](https://assets.ine.com/lab/learningpath/7ead824b81ce34f1201eb07925814d11e852cb5e0ee88fd1eddd66a100fa21f9.jpg)

**Step 7:** Observe the greetings strings in the output of the strings command. It is possible that welcome binary is calling greetings binary. So, replace the greetings binary with some other binary (say /bin/bash) which should then also get executed as root.

Delete greetings binary and then copy /bin/bash to its location and rename that to greetings.

![](https://assets.ine.com/lab/learningpath/4719edd51874a3596f116fea9495b23a64a509e86fd4fe6b8c349428c4b6f62c.jpg)

**Step 8:** Then, run the welcome binary again.

![](https://assets.ine.com/lab/learningpath/2a854f6a9fd56a51cbcff093fbbe3b0c57d651231dadbaec024bdb4c9e757e1a.jpg)

Student user got escalate to root user. Retrieve the flag kept in /root directory.

![](https://assets.ine.com/lab/learningpath/7b765e99563c056ac27062d294f5386302c821bbd8a47a70c099a209601bb7ff.jpg)

**Flag:** b92bcdc876d52108778e2d81f3b01494
