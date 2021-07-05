Spazi vettoriali e Cross Product
===

## World space vs Local Space
Tutto è uno spazio. Un punto nel mondo virtuale di unity, ha una transform, la quale risiede in un piano algebrico chiamato worldspace, ovvero uno spazio dove il centro è (0,0,0). Nel caso posizionassi un oggetto nella hierarchy, esso sarà gerarchicamente vincolato allo spostamento del centro del mondo, chiamando il sistema di coordinate World Space. 

Nel caso creassimo un oggetto dentro l'oggetto precendetemente creato, ovvero gerarchicamente come figlio, esso sarà vincolato al sistema di coordinate del padre, in quanto il padre è considerato come il centro del mondo, chiamando il sistema di coordinate del figlio, Local Space.

A logica, possiamo intuire che qualsiasi oggetto figlio, sia vincolato al sistema di coordinate del padre, considerando tale come centro del mondo. 

https://docs.unity3d.com/ScriptReference/Transform.html

 ```cs
 
 // World space pos
 Vector3 cubePos;
 Vector3 cameraPos;
 
 // Transform position from local space to world space
 cubePos.TransformPoint(Vector3 point);
 
 // Transform position from world psace to local space
 InverseTransformPoint
 
 ```
 
 ## Matrici
 
 Le matrici, come le conosciamo su unity, sono dei contenitori algebrici che contengono la posizione, la rotazione e come è scalato un oggetto in uno spazio.

Per esempio, i 3 valori a destra rappresentano la posizione dell'oggetto nel mondo, l'orientamento è definito dalla normale dei vettori nella prima sezione, mentre la lunghezza di essi, rappresenta la scala dell'oggetto.

E' importante soffermarsi che questa matrice è tridimensionale e funziona in 3 dimensioni.

```cs
//Orientations in unity
transform.right // X axis normalized
transform.up // Y axis normalized
transform.forward // Z axis normalized
```

Come abbiamo visto nello snippet sui world space e local space, le loro transformazioni sono fatti under the hood da delle matrici, le quali, permettono queste trasformazioni in maniera efficente e matematica, tramite poche moltiplicazioni.

![[Pasted image 20210224002809.png]] 

## Cross product
Il cross product, detta anche moltiplicazione tra due vettori, è anche detta geometricamente una moltiplicazione il quale risultato è un vettore di direzione perpendicolare ai due moltiplicati.

Se entrambi i vettori sono zero o sono perpendicolari, non esistono soluzioni, Unity ci tornera sempre un vettore 0.

![[Pasted image 20210224005911.png]]