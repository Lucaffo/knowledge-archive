Strategy Pattern
===

L'obiettivo è di rendere dinamica l'implementazione di algoritmi e funzioni, e cambiarli dinamicamente al runtime. Prevede che gli algoritmi siano intercambiabili tra di loro e che ritornino lo stesso tipo di oggetto alla fine.

Questo cosa comporta?

Mettiamo caso che ho una funzione che mi permette di ordinare una lista con una determiata strategia, questa funzione ritorna la lista ma ordinata.

Vorrei poter cambiare il metodo di ordinamento senza dover modificare il codice, ma innestando appunto una nuova strategia di ordinamento.

Come si implementa? Semplice!

Si utilizza un'interfaccia per poter descrivere un comportamento, o una funzione.

```csharp
public interface IFlyStrategy {
	public void fly();
}

public class FlyLikeDragonStrategy : IFlyStrategy {
	public void fly(){
		print("Fly Like a dragon! Yeaa!!");
	}
}

public class FlyLikeDuckStrategy : IFlyStrategy {
	public void fly(){
		print("Fly Like a duck! quack!!");
	}
}

class Duck {
	IFlyStrategy flyBehaviour;

	void SetFlyStrategy(IFlyStrategy fb){
		flyBehaviour = fb;
	}

	public void fly(){
		flyBehaviour?.fly();
	}
}
```

In questo modo abbiamo un comportamento dinamico e intercambiabile al runtime senza nessun problema.

Come hai potuto notare, questo pattern favorisce la composizione piuttosto che l'accoppiamento delle classi.