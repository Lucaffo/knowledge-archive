Decorator Pattern
===


E' un pattern che consente di modificare funzionalità ad oggetti già esistenti a runtime.

Il decoratore, avvolge l'oggetto originale restituendo lo stesso oggetto, ma con funzionalità modificate.

Visivamente è comparabile ad una cipolla, dove al centro abbiamo la classe principale, ed ogni strato è un decoratore, dove un decoratore avvolge un altro e così via.

La classe concreta finale sarà la combinazione o la composizione di tutti questi decoratori ritornato dall'ultimo anello.

![](decorator.png)

Un decoratore è e possiede l'oggetto del componente che avvolge, provvedendo un'alternativa flessibile per aggiungere funzionalità senza avere una gerarchia di classi.

Non è da utilizzare in tutti i casi, bisogna capire bene quando usarla e quando non, e l'implementazione segue una linea del genere. Prima di tutto si stabilisce la classe del componente e del decoratore.

```csharp
// Componente
public abstract class Bevanda {
	public abstract int cost(); // Ritorna il costo della bevanda
}

// Decoratore
public abstract class DecoratoreBevanda : Bevanda {
	public abstract int cost(); // Ritorna il costo della bevanda
}
```

Sembra ancora strano vista dalla prima implementazione, ma nell'essenza è quello che fa un decoratore, **simula il comportamento** della Bevanda, in modo da comportarsi come essa. Passiamo all'implementazione concreta.

```csharp
// Implementazione di una bevanda
public class Caffe : Bevanda {
	public float cost(){
		return 1f; // Euro
	}
}

// Implementazione del decoratore
public class DecoratoreLatte : DecoratoreBevanda {
	
	// Riferimento alla bevanda di base
	private Bevanda _bevanda;

	// Costruttore
	DecoratoreLatte(Bevanda bevanda){
		_bevanda = bevanda;
	}

	// Aggiunge il costo del latte alla bevanda
	public int cost(){
		_bevanda.cost() + 0.50f;
	}
}
```

In questo esempio abbiamo visto come può essere utile utilizzare il Decorator Pattern e come le funzionalità siano rimaste ma modificate, come per esempio, il prezzo che cambia mano a mano che aggiungiamo componenti aggiuntivi.

Quando è utile utilizzarlo? Qual'è il coding smell che dovrebbe allertarci?

-   Quando le proprietà e i comportamenti di una classe devono essere modificabili al runtime.
-   Quando durante la progettazione ci ritroviamo davanti ad una **Exploding Class Hierarchy**.
-   Quando la prima soluzione che ti viene in mente è quella di aggiungere tanti booleani.