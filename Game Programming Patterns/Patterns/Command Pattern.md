Command Pattern
===

E' essenzialmente un pattern che consiste di impacchettare una chiamata a funzione all'interno di un'oggetto. Possono ricordare molto una callback, e non è buttata tanto di fuori, perché fa parte dello stesso parco alla fine. Di fatto la gang of four la chiamata proprio "Una callback object oriented".

E' molto comune accoppiare questo pattern a qualcosa che invoca i comandi, come un dispositivo di input. Un bottone che se premuto **invoca** il **comando** che abbiamo legato ad esso.

Abbiamo due componenti principali:

-   **Invoker** (Colui che invoca i comandi)
-   **Command** (Il comando)
-   **Receiver** (Colui che riceve le conseguenze del comando)

```csharp
public abstract class ICommand{
	public void execute();
	public void unexecute();
}

public class LightOnCommand : ICommand{
	public void execute(){
		LightController.turnOn();
	}
	public void unexecute(){
		LightController.turnOff();
	}
}

...

public class Invoker
{
	ICommand on;
	ICommand off;
	ICommand up;
	ICommand down;		

	public Invoker(ICommand on, ICommand off, ICommand up, ICommand down){
		...
	}
	
	public void clickOn(){
		this.on.execute();
	}

	...
}
```

Due appunti sulla creazione dell'invoker:

-   I Comandi chiamali con il **nome dell'azione** o del **tasto** (Se si tratta di dispositivi di input).
-   Evita metodi "setCommand", se non prevedi che i comandi variano, piuttosto mettili dentro il **costruttore**.
-   Se hai bisogno di avere una cronologia di comandi lanciati, crea una coda di comandi.