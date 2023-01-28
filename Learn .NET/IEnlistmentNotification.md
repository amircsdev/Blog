# IEnlistmentNotification Interface

**IEnlistmentNotification** is an interface in the System.Transactions namespace in C# that allows for the creation of **custom enlistment classes**. It is used to notify a resource manager (such as a database) of a transaction's progress and to coordinate the outcome of the transaction with the resource manager. The interface has three methods: **Commit**, **InDoubt**, and **Rollback**, which are called by the Transaction Manager at various stages of the transaction's life-cycle.


Here is an example of a class that implements the IEnlistmentNotification interface:

``` C#
class MyEnlistment : IEnlistmentNotification
{
    public void Commit(Enlistment enlistment)
    {
        // Perform any necessary cleanup or release of resources here
        Console.WriteLine("Transaction has been committed.");
        enlistment.Done();
    }

    public void InDoubt(Enlistment enlistment)
    {
        // Perform any necessary cleanup or release of resources here
        Console.WriteLine("Transaction is in doubt.");
        enlistment.Done();
    }

    public void Prepare(PreparingEnlistment preparingEnlistment)
    {
        // Perform any necessary preparation here
        Console.WriteLine("Transaction is being prepared.");
        preparingEnlistment.Prepared();
    }

    public void Rollback(Enlistment enlistment)
    {
        // Perform any necessary cleanup or release of resources here
        Console.WriteLine("Transaction has been rolled back.");
        enlistment.Done();
    }
}
```

And here is an example of how to enlist an instance of the class in a transaction:

``` C#
using (TransactionScope scope = new TransactionScope())
{
    MyEnlistment myEnlistment = new MyEnlistment();
    Transaction.Current.EnlistVolatile(myEnlistment, EnlistmentOptions.None);
    // Perform any necessary work here
    scope.Complete();
}
```

This example creates a new TransactionScope and creates an instance of MyEnlistment class. Then it enlists it in the current transaction using the EnlistVolatile method and passing the instance of MyEnlistment and EnlistmentOptions.None. Then it performs any necessary work and calls Complete() to indicate the transaction should be committed.
