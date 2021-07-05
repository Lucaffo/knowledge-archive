State Pattern
===

Finite States Machine
=====================

> _Una Finite State Machine è **un'astrazione** di una macchina in grado di essere in uno stato assegnato in qualsiasi momento._

Come il nome suggerisce esiste solo un **set finito di stati,** ovvero dove la macchina può essere in un qualsiasi momento. Inoltre la macchina può esistere ed esiste sempre e in **un solo stato alla volta.**

Lo state pattern permette di cambiare il **comportamento della classe**, quando il suo **stato interno** cambia, **cambiando la classe**.

il compito di una state machine è di:

-   Avere una **lista di stati possibili** intercambiabili
-   Stabilire le **condizioni** sulle quali questi stati cambiano
-   Primo stato, o **stato iniziale** dal quale è possibile estendere o stati diversi

![https://gameprogrammingpatterns.com/images/state-flowchart.png](https://gameprogrammingpatterns.com/images/state-flowchart.png)

Questa definizione di pattern è solo una delle tante spiegate in una teoria chiamata **Automata Theory**, la quale spiega come il comportamento di un automa è composto da stati intercambiabili.

UML
---

Abbiamo un contesto e tanti diversi stati. Per essere intercambiabili dall'interno del contesto, lo stato deve derivare da una interfaccia di stato generica. Quali metodi implementare nell'interfaccia? Dipende, solitamente sono metodi che riguardano gli eventi e le azioni che servono per passare da uno stato a stato.

Inoltre uno stato concreto, dovrebbe avere accesso al contesto per poter cambiare stato autonomamente.

![https://dotnettrickscloud.blob.core.windows.net/img/designpatterns/state-design-pattern.png](https://dotnettrickscloud.blob.core.windows.net/img/designpatterns/state-design-pattern.png)

Una volta che lo stato viene cambiato dal contesto, il programma continuerà a funzionare correttamente perché l'implementazione di uno stato differente è lo stesso. La parte più interessante "request", permette di richiedere e cambiare lo stato attuale.

Implementazione
---------------

La più semplice implementazione di una macchina a stati finiti è tramite le enums e gli switch statements.

```csharp
enum CharacterStates {
	STANDING,
	DUCKING,
	JUMPING,
	DIVING
}

CharacterStates _currentState = CharacterStates.STANDING;

switch (_currentState){
		case STANDING:
				if(jump){
					_currentState = JUMPING;
					break;
				}
				....
}
```

E' l'implementazione più semplice, ma solo se abbiamo stati semplici. Se il tutto inizia a complicarsi, allora bisogna iniziare a pensare di orientare questo pattern agli oggetti.

Implementazione in OOP
----------------------

Tutto quello che ci serve è un'interfaccia che funga da stato generico.

```csharp
public interface CharacterState{
		public void update();
		public void handleInput(Character character, Input inputs);
}

public class StandingState : CharacterState{
		public void handleInput(Character character, Input inputs){
				if(inputs.getKeyDown("X")){
						character.currentState = new JumpingState();
				}
		}
}
```

In questo modo ci permette di attuare al meglio l'applicazione del **principio di singola responsabilità**.

### Cambiare stato

Come hai potuto notare, creo un'instanza di uno stato ogni volta che lo cambio. Questo potrebbe portare a problemi di performance se non usato nel giusto contesto. In linea di massima esistono due modi per creare uno stato.

-   **Dynamic States**. Sono gli stati che vengono creati sul momento, il loro vantaggio sta che se all'interno gestiamo dei valori particolari, non dobbiamo gestire un **reset dei valori**. Unico svantaggio che potrebbero essere **expansive per il garbage collector**.
-   **Static States.** Sono gli stati che vengono creati solo all'inizio e resi statici. Questo ci permette di accedere a quegli stati senza inizializzarli ogni volta. Il vantaggio sta nelle performance, ma il reset dei valori va fatto manualmente. Inoltre, se volessimo riutilizzare gli stati per altri oggetti non lo potremmo fare.

Concurrent States machine
=========================

Si parla di **concurrent state machine**, quando abbiamo bisogno di più macchine a stato finito per più componenti del sistema. Quando vogliamo che **due sistemi vengono azionati in contemporanea** e che non interagiscano tra di loro ma usano gli stessi input. Un'esempio può essere che ho bisogno di una state machine per il movimento del player e una state machine per le interazioni del player. Nel caso in cui volessi sparare quando mi muovo, avrei bisogno di uno stato armato/non armato per ogni stato di movimento, una cosa che ci porta ad una **class explosion**.