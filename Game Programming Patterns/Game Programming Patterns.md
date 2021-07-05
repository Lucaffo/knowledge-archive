Architetture, Performance e Giochi
==================================

Un'architettura software permette di organizzare meglio la struttura del codice, in modo da poter garantire funzionalità aggiuntive nel modo più semplice possibile. Esistono molti design di queste architetture e vanno usate quando la situazione ne necessita.

**Una buona architettura si _adatta_ bene al cambiamento.** Cioè nel cambiare la logica finale senza doverci preouccupare della logica principale. Questo però può portare a dei problemi di performance, dovuto da procedure complesse sebbene stabili. Un dato positivo però c'è; al mondo d'oggi è davvero difficile che un design architetturale complesso inplichi un'abbassamento delle performance se si lavora su progetti non troppo complessi. Questo è dovuto dal fatto che le tecnologie sono in continua evoluzione, soprattutto dal punto di vista della potenza di calcolo.

**Non generalizzare, quando non necessario.** Noi sviluppatori tendiamo a generalizzare qualsiasi cosa, anche quando non c'è nè bisogno. Non è detto che il codice che usi per l'interfaccia grafica sia per forza riutilizzabile o se hai davvero bisogno di creare una classe generale per il danno. Non specularizzare che ti serve quel livello di astrazione in più quando non necessario.

**Preferire la composizione all'accoppiamento.** Questo significa che è necessario disaccoppiare i riferimenti al codice quando possibile. Non vorrei che tutto il codice smettesse di funzionare se elimino una variabile, e questo non significa aggiungere try catch sia chiaro! Significa letteralmente un buon uso di interfaccie e astrazioni. Questo ci permette che una volta cambiato una linea di codice ne dobbiamo cambiare il meno possibile.

**Semplicità**. Mantenere semplice il codice consiste nel mantenerlo più pulito possibile, ogni funzionalità ha il suo posto e non è una massa uniforme di variabili e funzioni unite insieme. Un codice pulito è quello contestualizzato e separato nel miglior modo possibile.

Design patterns
===============
[[Strategy Pattern]]
[[Observer Pattern]]
[[Decorator Pattern]]
[[Factory Pattern]]
[[State Pattern]]
[[Decorator Pattern]]
[[Command Pattern]]
[[Dipendency Injection Pattern]]
[[Adapter Pattern]]