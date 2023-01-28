# what is ICloneable in c#

ICloneable is an interface in C# that defines a single method, Clone, which creates a new object that is a copy of the current instance. Classes that implement the **ICloneable interface** are able to create a copy of themselves. The actual implementation of the Clone method is up to the class that implements the interface. It can create a shallow copy or a deep copy, depending on the needs of the class.

Here's an example of a class, Person, that implements the ICloneable interface:

``` C#
class Person : ICloneable
{
    public string Name { get; set; }
    public int Age { get; set; }

    public object Clone()
    {
        return this.MemberwiseClone();
    }
}
```

In this example, the **Person** class has two properties, **Name** and **Age**. The class implements the ICloneable interface and the Clone method creates a shallow copy of the current instance using the **MemberwiseClone** method.

You can create a new instance of the Person class and then use the Clone method to create a copy of it:

``` C#
Person original = new Person { Name = "John", Age = 30 };
Person copy = (Person)original.Clone();
```

In this example, the original and copy variables will refer to two separate instances of the Person class, but their properties will have the same values (Name = "John" and Age = 30).
