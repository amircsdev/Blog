# an example about EntityFramework.BulkInsert

Here is an example of how to use the **EntityFramework.BulkInsert** library to insert a large number of records into a database table using the Entity Framework:

``` C#
using (var context = new MyDbContext())
{
    var entities = new List<MyEntity>();
    // add entities to the list

    context.BulkInsert(entities);
}
```

In this example, MyDbContext is the database context, MyEntity is the entity type to be inserted, and entities is a list of entities to be inserted into the database table. The BulkInsert method is an extension method that is added to the context by the EntityFramework.BulkInsert library, and it takes care of inserting the entities into the database in a performant way.

Note that you should install the package and add the reference to your project, you can install it via nuget package manager by running the command:

``` C#
install-package EntityFramework.BulkInsert
```
