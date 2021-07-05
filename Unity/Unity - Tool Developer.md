Tool Developer in Unity
===

### Cos'è un tool developer
In pratica è uno sviluppatore il quale target di udienza non sono i giocatori ma gli altri sviluppatori o designers, in modo tale da velocizzare il workflow di creazione e modifica dei progetti. 

## Custom Editor Scripts
E' possibile estendere un tipo in modo da modificarne il modo in cui viene visto e in cui interagiamo tramite l'inspector.

Per farlo è necessario estendere da `UnityEditor` la classe padre `Editor` e fare l'override del suo metodo `OnInspectorGUI`. 

```cs
using UnityEngine;

[CustomEditor(typeof(BarrelType))]
public class BarrelTypeEditor : Editor 
{
	public override void OnInspectorGUI()
	{
		// Draw the default inspector gui
		base.OnInspectorGUI();
	
		// Override this function to override the gui on inspector
	}
}
```

E' convenzione usare il suffisso Editor in fondo al nome dello script per indicare che questo script ha a che vedere con l'editor, inoltre si usa anche una cartella apposita "Editor". 

### Problemi che possono sortire se si accede e si modifica direttamente i valori da il nostro custom inspector.

```cs

using UnityEngine;

[CustomEditor(typeof(BarrelType))]
public class BarrelTypeEditor : Editor 
{
	public override void OnInspectorGUI()
	{
		//Wrong way
		BarrelType barrel = target as BarrelType;
		barrel.radius = EditorGUILayout.FloatField("radius", barrel.radius );
		barrel.damage = EditorGUILayout.FloatField("damage", barrel.damage );
		barrel.color = EditorGUILayout.ColorField("color", barrel.damage );	
	}
}

```

1) Una volta modificati i valori non è possibile tornare indietro. (Ctrl + Z non funziona), quindi in caso di errore non puoi tornare allo stato precendente.
2) E' comodo aver un modo per ripristinare i valori al loro stato originale.
4) Non supporta la multiselezione di oggetti simili tra loro.

```cs
using UnityEngine;

[CustomEditor(typeof(BarrelType))]
public class BarrelTypeEditor : Editor 
{
	public override void OnInspectorGUI()
	{
		//Wrong way
		BarrelType barrel = target as BarrelType;
		
		// anche se facessimo un nuovo raggio, abbiamo bisogno di fare in modo che 
		// l'undo system di unity sia in grado di vederlo e di poter fare "Undo" su questo
	    // field
		float newRadius = EditorGUILayout.FloatField("radius", barrel.radius );
		if(newRadius != barrel.radius)
		{
			Undo.RecordObject(barrel, "change barrel radius");
			barrel.radius = newRadius; // UN SACCO DI BOILERPLATE
		}
		
		barrel.damage = EditorGUILayout.FloatField("damage", barrel.damage );
		barrel.color = EditorGUILayout.ColorField("color", barrel.damage );	
	}
}
```

Esiste una maniera più sicura per poterlo fare in modo da evitare boilerplate.

```cs
using UnityEngine;

[CanEditMultipleObjects]
[CustomEditor(typeof(BarrelType))]
public class BarrelTypeEditor : Editor 
{
	SerializedObject so;
	
	// SerializedPropertes of the BarrelType properties.
	SerializedProperty propRadius;
	SerializedProperty propDamage;
	SerializedProperty propColor;

	// Called everytime we select this object
	void OnEnable()
	{
		// The target object serialized
		so = serializedObject;
		
		// Get the serialized properties of the target object
		propRadius = so.FindProperty("radius");
		propDamage = so.FindProperty("damage");
		propColor = so.FindProperty("color");
	}

	// This function is looping multiple times.
	public override void OnInspectorGUI()
	{
		// Update the serialized target object 
	    so.Update()
	 	
		// Setup properties to automatically support, serialization, multiselection and other usuful stuff.
		EditorGUILayout.PropertyField(propRadius);	
		EditorGUILayout.PropertyField(propDamage);
		EditorGUILayout.PropertyField(propColor);	
		
		// Apply the properties 
		s.ApplyModifiedProperties();
	}
}
```

problemi risolti:
1) L'Undo system è implementato automaticamente
2) Supporto alla multiselezione e alla multimodifica

Tutto questo praticamente a gratis, grazie alle properties, che sono molto utili per bindare i valori dell'oggetto all'UI dell'inspector, in quanto ci da a disposizione un sacco di funzionalità che avremmo dovuto implementare a mano.

Inoltre `EditorGUILayout.PropertyField(propRadius);` prende automaticamente il tipo di variabile, se serializzabile, associando il picker più funzionale possibile. Il suo compito è bindare automaticamente la proprietà al campo dell'inspector, inoltre prende automaticamente e usa i [Property Drawers](https://docs.unity3d.com/ScriptReference/PropertyDrawer.html) bindati a quella properties.

Tips:

Se hai bisogno di avere il controllo e sapere quando hai cambiato un campo, sappi che è possibile perché `so.ApplyModifiedProperties()` ritorna un booleano che corrisponde proprio a true quando c'è stato un cambiamento.
Esiste il caso remoto in cui quando applichi un valore a un qualcosa hai bisogno di fare anche altre operazioni. Ricordatelo può servire in futuro.

```cs

// This function is looping multiple times.
public override void OnInspectorGUI()
{
	// Update the serialized target object 
	so.Update()
   
    // ... stuff

	// Apply the properties 
	if(s.ApplyModifiedProperties())
	{
		// Something changed
	}
}

```

## Menu Items
I menu item sono gli elementi che stanno in cima a unity che possono essere selezionati per aprire nuove finestre o creare nuovi oggetti in scena.

 `MenuItem` è prima di tutto un attributo che va applicato alle funzioni.
 
 ```cs
 public static class Snapper
 {
    [MenuItem("Edit/Snap Selected Objects")]
 	public static void SnapTheThings()
	{
		// The game object selected in scene
		GameObjects[] gameObjects = Selection.gameObjects;
		
		foreach(GameObject gameObject in gameObjects)
		{
			// Round the position of the object
			gameObject.transform.position = gameObject.transform.position.Round();
		}
	}
		
	// Extended functionality of a vector3 to accept a round function
	public static Vector3 Round(this Vector3 v)
	{
		v.x = Mathf.Round(v.x);
		v.y = Mathf.Round(v.y);
		v.z = Mathf.Round(v.z);
		
		return v;
	}
 }
 
 ```
 
 ### Un grandissimo problema
 L'editor una votla effettuato un cambiamento con questo tool, non riesce a vedere che è stato effettuato un cambiamento effettivo alla scena, di conseguenza non viene marchiato per essere salvato e il nostro stato non verrà salvato.
 
 Per risolvere il problema è necessario registrarlo la funzionalità di  `Undo` prima di modificare il valore con  `Undo.RecordObject` passando come parametro quale componente particolare vogliamo flaggare come da "salvare" o aggiornare dal serializzatore di unity.
 
  ```cs
 [MenuItem("Edit/Snap Selected Objects")]
public static void SnapTheThings()
{
	// What to say when we undo
	const string UNDO_STR_SNAP = "snap selected objects";

	// The game object selected in scene
	GameObjects[] gameObjects = Selection.gameObjects;

	foreach(GameObject gameObject in gameObjects)
	{
		// Register for undo and recording for the transform component
		Undo.RecordObject(go.transform, UNDO_STR_SNAP);
	
		// Round the position of the object
		gameObject.transform.position = gameObject.transform.position.Round();
	}
}
 ```
 
 Ora unity quando useremo quella funzione dal menu, verrà segnato come se dovessimo salvare lo stato del gioco, inoltre è adesso possibile fare operazione di UNDO e REDO.
 
 ### Menu Hotkeys o Shorcut
 E' possibile assegnare a un  `MenuItem` un hotkey o una shortcut in modo da chiamare la funzionalità velocemente.
 Per i significati dei simboli è necessario guardare la documentazione ufficiale unity [MenuItem](https://docs.unity3d.com/ScriptReference/MenuItem.html).
 
   ```cs
 [MenuItem("Edit/Snap Selected Objects &s")] // alt + s
public static void SnapTheThings()
{
 ```
 
 ### Validazione della funzione
 Alla proprietà MenuItem è possibile associare una funzione booleana in modo tale da non poterla usare nei casi in cui non è specificato usarla. (Magari per usarla hai necessariamente bisogno di selezionare uno o più oggetti di determinati tipi o sapere se esiste un oggetto in scena etc..)
 
  ```cs
 [MenuItem("Edit/Snap Selected Objects", isValidateFunction:true)]
public static bool SnapTheThingsValidate()
{
	return Selection.gameObjects > 0;
}
 ```
 
 ### Posizionamento del menu item
 Ricordati che è possibile inserire questo item in qualsiasi sottomenu qualsivoglia e crearlo anche di punto in bianco.
 
   ```cs
 [MenuItem("MyGameTools/DesignerTools/Snap Selected Objects"]
 ```
 
 ## Editor Window
 E' inoltre possibile creare una finestra come l'inspector che si muova o rimanga fissa dove è possible costruire sopra i nostri strumenti ed estendere le funzionalità dell'editor.
 
 Esempio:
 
```cs
public class SnapperTool : EditroWindow 
{
	// In practical, this menu item is used to open this window in the editor. 
	// Is super useful if you lost the reference o close window.
	// Get window open only one window at time, this means that will autofocus on already opened window if exists.
	[MenuItem("Tools/SnapperTool")]
	public static void OpenWindow() => GetWindow<SnapperTool>("Title of the window");
	
	void OnEnable()
	{
		// When the selection is changed, repaint the ui
		Selection.selectionChanged += Repaint; // Repaint() is a gui function from EditorWindow, it will repaint the interface
	}
	
	void OnDisable()
	{
		Selection.selectionChanged -= Repaint;
	}
	
	void OnGUI()
	{
		GUILayout.Label("Hello world from window!");
		
		// Button is disabled if there are not selected object in scene
		using( new EditorGUI.DisabledScope(
			// Bool condition here
			Selection.gameObject.Length == 0
		)){
			if(GUILayout.Button("Press me"))
			{
				Debug.log("Do something");
			}
		}
	}
}
```

Una cosa importantissima che vedrai spesso è che l'UI espone un sacco di metodi per iscriversi a callback tramite observer pattern. E' una cosa fighissima e permette di alzare il livello di cose che puoi fare di tanto.

## EditorPrefs
Serve per storare informazioni e preferenze tra sessioni di lavoro, per variabili dell'editor.

[Editor Prefs](https://docs.unity3d.com/ScriptReference/EditorPrefs.html).

Questa cosa è utile in molti casi in quanto, se volessimo salvare la posizione di un tool in scena e la sua configurazione.

```cs
void OnEnable()
{
	// Load saved configuration
	// Key flag and default value if not found
	points = EditorPrefs.GetFloat("PROJECT_THING_PLAYER_POINTS", 1f); 
}

void OnDisable()
{
 	// Save current configuration on exit
	EditorPrefs.SetFloat("PROJECT_THING_PLAYER_POINTS", points);
}
```

## EditorPrefs vs ScriptableObject
Entrambi sono dei metodi validi per salvare informazioni tra sessioni di lavoro. L'unica differenza tra i due è che le EditorPrefs sono sharate tra tutti i progetti in locale, mentre lo scriptable object è locale al progetto.

