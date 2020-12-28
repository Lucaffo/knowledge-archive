Observer Pattern
===

Molti paradigmi di programmazione legati agli eventi sono riconducibili a questo pattern. Esistono due entità legati ad uno specifico evento.

-   **Observable.** Colui che deve essere osservato, colui che controlla se l'evento accade. Gestisce una **lista** di Observer.
-   **Observer.** Colui che osserva, che si registra, all'observable in modo tale che al cambiamento venga notificato del cambiamento.

Per l'implementazione abbiamo le due entità astratte in due interfaccie separate.

```csharp
public interface IObservable{
	void subscribe(IObserver obs);
	void unsubscribe(IObserver obs);
	void notify(); // This function notify all the observers
}

public interface IObserver{
	void update(); // Called when notify
}
```

L'observable ha due metodi principali per aggiungere e rimuovere un'observer, ad una ipotetica lista all'interno dell'observable implementato.

Notify è una funzione che generalmente cicla la lista di observer e chiama il loro metodo update.

Se non è chiaro, qui sarà mostrata un'implementazione di queste interfaccie.

```csharp
public class WeatherStation : IObservable {
	private List<WeatherDisplay> _weatherDisplays = new List<WeatherDisplay>();
	private float _temperature;	

	public void SubscribeDevice(WeatherDisplay observer){
		_weatherDisplays.Add(observer);
	}

	public void UnsubscribeDevice(WeatherDisplay observer){
		_weatherDisplays.Remove(observer);
	}
	
	public void GetTemperature(){
		_temperature = ...;
		
		.... confronta le temperature ...

		// Notifica se la temperature è cambiata
		if(changed) notify();
	}
	
	public void notify(){
		foreach(WeatherDisplay weatherDisplay : _weatherDisplays){
			weatherDisplay.Update(_temperature);
		}
	}
}

public class WeatherDisplay : IObserver {

	private int _id;
	
	WeatherDisplay(int id){
		_id = id;
	}
	
	public void Update(float temperature){
		// Update the display
		print("WeatherDisplay#"+_id+" temperature " + temperature);
	}
}
```