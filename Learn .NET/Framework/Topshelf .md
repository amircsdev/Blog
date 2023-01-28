# what is Topshelf in .Net?

**Topshelf** is a framework for creating **Windows services using the .NET framework**. It allows developers to write a service application using a simple, console-based interface and then easily install and run that application as a Windows service. Topshelf provides a simple and convenient way to create and manage Windows services, without the need for complex configuration or setup.

Here is an example of a simple Topshelf service that writes a message to the console every 5 seconds:

``` c#
using System;
using Topshelf;

namespace MyService
{
    class Program
    {
        static void Main(string[] args)
        {
            var exitCode = HostFactory.Run(x =>
            {
                x.Service<MyService>(s =>
                {
                    s.ConstructUsing(name => new MyService());
                    s.WhenStarted(tc => tc.Start());
                    s.WhenStopped(tc => tc.Stop());
                });
                x.RunAsLocalSystem();

                x.SetDescription("My Service Description");
                x.SetDisplayName("MyService");
                x.SetServiceName("MyService");
            });

            int exitCodeValue = (int)Convert.ChangeType(exitCode, exitCode.GetTypeCode());
            Environment.ExitCode = exitCodeValue;
        }
    }

    public class MyService
    {
        public void Start()
        {
            while (true)
            {
                Console.WriteLine("MyService is running.");
                System.Threading.Thread.Sleep(5000);
            }
        }

        public void Stop()
        {
            Console.WriteLine("MyService is stopping.");
        }
    }
}
```

In this example, the MyService class is responsible for the actual service logic. The Start method runs in a loop, writing a message to the console every 5 seconds. The Stop method is called when the service is stopped.

The Main method sets up the Topshelf service configuration, including setting the service description, display name, and service name. It also specifies that the service should run as the local system user.

You can install and start the service using the command-line tool provided by Topshelf, like so:

``` cmd
MyService.exe install
MyService.exe start
```

You can stop and uninstall the service using the following command

``` cmd
MyService.exe stop
MyService.exe uninstall

```

This is a basic example, Topshelf offers a lot more functionalities like, dependency injection, custom command-line arguments, logging, and more.
