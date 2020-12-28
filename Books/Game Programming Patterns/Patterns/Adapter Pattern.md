Adapter Pattern
===

L'Adapter pattern è un pattern che permette di **adattare due interfaccie** diverse o incompatibili. Solitamente basta pensare ad **una presa**, ha un solo input e un solo output, e gli adattatori permettono di adattare un input per renderlo simile ad un output specifico.

-   NON confondere, con la logica di un trasformatore. Un adattatore, deve adattare un input in uno specifico output, non modificarlo radicalmente.
-   L'adattatore è necessario quando la logica iniziale e finale hanno una logica simile, ma incompatibili come metodi. (Immagina due parti di un puzzle. Sono entrambi parte del puzzle ma le loro giunture sono incompatibili. Crei un pezzo di puzzle che possa attaccarli)
-   Aggiunge un livello di indirezzione; chiamiamo qualcosa che chiama un'altra cosa, in questo caso adattando i dati di ingresso delle funzioni.

```csharp
public interface ITarget
{
	void request();
}

...

ITarget target = new Adapter(new Adaptee());
target.request();

class Adapter : ITarget 
{
		// Adapting implementation
		Adapter(Adaptee adaptee){
			...
		}

		public void request()
		{
			this.adaptee.specificRequest();
		}
}
```