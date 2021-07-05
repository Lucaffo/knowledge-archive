Factory Pattern
===

Consiste nell'incapsulare l'instanziamento di un oggetto attorno ad una chiamata di funzione ad una classe statica. Instanziare diversi oggetti seguendo una logica ben precisa, senza incasinare il codice e magari usandolo da più parti del codice senza replicare la il codice di logica. Permette di costruire oggetti usando logiche customizzate e/o utilizzando sottotipi diversi.

Il pattern è molto semplice e si implementa in questo modo:

```csharp
public interface IProduct
{
    string GetName();
    string SetPrice(double price);
}

public class Phone : IProduct
{
    private double _price;

    public string GetName()
    {
        return "Apple TouchPad";
    }

    public string SetPrice(double price)
    {
        this._price = price;
        return "success";
    }
}

/* Almost same as Factory, just an additional exposure to do something with the created method */
public abstract class ProductAbstractFactory
{
    protected abstract IProduct MakeProduct();

    public IProduct GetObject() // Implementation of Factory Method.
    {
        return this.MakeProduct();
    }
}

public class PhoneConcreteFactory : ProductAbstractFactory
{
    protected override IProduct MakeProduct()
    {
        IProduct product = new Phone();
        //Do something with the object after you get the object.
        product.SetPrice(20.30);
        return product;
    }
}
```

Un Abstract factory pattern è essenzialmente un qualcosa che ci permette di gestire un set di factory diversi, che gestiscono oggetti simili. E' davvero imporante capire che si implementa per oggetti appartenenti alla stessa famiglia di oggetti. E un pattern factory, ma con più metodi di factory diversi