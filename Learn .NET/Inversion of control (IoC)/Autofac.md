# what is Autofac?

**Autofac** is an open-source **Inversion of Control (IoC)** container for .NET. It is a dependency injection (DI) container that helps manage the dependencies between objects in a program, making the code more modular and easier to test.

An IoC container is a library that manages the creation and lifetime of objects in a program, and it provides a way to request an instance of a certain type, known as a dependency. The container will then create the object and any of its dependencies and return an instance of the requested type. This allows objects to be decoupled from the objects they depend on, making the code more modular and easier to maintain and test.

Autofac provides a wide range of features, including support for constructor injection, property injection, and method injection, as well as support for decorators and interceptors. It also provides features for managing the lifetime of objects created by the container, such as singleton, per-thread, and per-request.

In addition, Autofac is a lightweight and high-performance container, it has a rich set of features, and is easily extensible. It is widely used in various projects, and it's also easy to integrate with other frameworks such as ASP.NET, WCF, and MVC.

## what is Autofac.ContainerBuilder?

**Autofac.ContainerBuilder** is a class in the **Autofac library**, which is a dependency injection container for .NET. The ContainerBuilder class is used to configure and build an Autofac container.

It provides methods for registering types and instances, as well as for configuring the lifetime and scope of objects created by the container. 

Once the container is configured, the Build() method is called to create an instance of the container, which can then be used to resolve dependencies and create objects.

It's a central class that allow you to register components in the container, you can use it to configure Autofac, specify the types that should be created when a dependency is requested, and specify the lifetime of those instances.

For example, the following code creates an instance of the **ContainerBuilder class**, registers a few types, and then creates an Autofac container:

``` C#
var builder = new ContainerBuilder();
builder.RegisterType<MyService>().As<IMyService>();
builder.RegisterType<MyRepository>().As<IMyRepository>();
builder.RegisterType<MyController>();
var container = builder.Build();
```
In this example, MyService, MyRepository, and MyController are registered with the container, and the container is configured so that when a dependency of type IMyService is requested, an instance of MyService will be created, and similarly for MyRepository and MyController.
