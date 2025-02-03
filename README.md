WMAP è uno **scanner** di **vulnerabilità** per **applicazioni web potente** e ricco di funzionalità
che può essere utilizzato per **automatizzare l'enumerazione** dei **server** **web** e la scansione delle applicazioni web per la ricerca di vulnerabilità.

E’ completamente **integrato** con **MSF**, che di conseguenza ci **permette** di
**eseguire** la **scansione** delle vulnerabilità delle applicazioni web **dall'interno** di **MSF.**

1. **load wmap**
2. **wmap_** premendo tab e non invio vedremo quali comandi possiamo lanciare
3. **wmap_sites -a IP_TARGET** mappa il sito target
    1. **wmap_sites -l** mostra info
4. **wmap_targets -t HTTP://IP_TARGET** imposta il target
    1. **wmap_targets -l** mostra info
5. **wmap_run -t** mostra tutti i moduli che il tool utilizzerà contro il target
6. **wmap_run -e** avvia l’esecuzione dei moduli
    1. i moduli con risultati positivi hanno un segno + alla loro sinistra
7. **wmap_vulns -l** mostra vulnerabilità trovate
