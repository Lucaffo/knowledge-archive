Essenzialmente, è un pattern che in sostanza permette di iniettare una dipendenza software dentro il suo utilizzatore, senza che l'utilizzatore debba avere un diretto accesso o metodo di creazione di quest'ultima.

La DIP ( Dependency Inversion Principle ), ammette che i moduli di alto livello non dovrebbero dipendere da quelli di basso livello, entrambi dovrebbero dipendere da astrazioni. Le astrazioni non dipendono dai dettagli. I Dettagli devono dipendere dalle astrazioni.

Principi fondamentali.

-   Dipendere da un'astrazione piuttosto che da una implementazione.
-   Dipendere dall'Argomento del costruttore. (Constructor Injection)

![](dip.png)