# Monitor And Lock In C#

The Monitor class in C# provides a mechanism for synchronizing access to an object. The Enter and Exit methods are used to acquire and release a lock on an object, respectively. The TryEnter method can be used to attempt to acquire a lock on an object, but return immediately if the lock is not available.

The lock statement in C# is a shorthand for using the Monitor class to acquire and release a lock on an object. The general syntax for using the lock statement is:

Monitor and lock is the way to provide thread safety in a multithreaded application in C#. Both provide a mechanism to ensure that only one thread is executing code at the same time to avoid any functional breaking of code.

## LOCK

C# Lock keyword ensures that one thread is executing a piece of code at one time. The lock keyword ensures that one thread does not enter a critical section of code while another thread is in that critical section.

Lock is a keyword shortcut for acquiring a lock for the piece of code for only one thread.

``` C#
namespace Monitor_Lock  
{  
    class Program  
    {  
        static readonly object _object = new object();  
  
        static void TestLock()  
        {  
              
            lock (_object)  
            {  
                Thread.Sleep(100);  
                Console.WriteLine(Environment.TickCount);  
            }  
        }  
  
        static void Main(string[] args)      
        {  
            for (int i = 0; i < 10; i++)  
            {  
                ThreadStart start = new ThreadStart(TestLock);  
                new Thread(start).Start();  
            }  
  
            Console.ReadLine();  
        }  
    }  
}  
```

## Monitor

Monitor provides a mechanism that synchronizes access to objects. It can be done by acquiring a significant lock so that only one thread can enter in a given piece of code at one time. Monitor is no different from lock but the monitor class provides more control over the synchronization of various threads trying to access the same lock of code.

Using a monitor it can be ensured that no other thread is allowed to access a section of application code being executed by the lock owner, unless the other thread is executing the code using a different locked object.

The Monitor class has the following methods for the synchronize access to a region of code by taking and releasing a lock,
- Monitor.Enter 
- Monitor.TryEnter
- Monitor.Exit.

Monitor locks objects (that is, reference types), not value types. While you can pass a value type to Enter and Exit, it is boxed separately for each call.

``` C#
namespace Monitor_Lock  
{  
    class Program  
    {  
        static readonly object _object = new object();  
  
        public static void PrintNumbers()  
        {  
            Monitor.Enter(_object);  
            try  
            {  
                for (int i = 0; i < 5; i++)  
                {  
                    Thread.Sleep(100);  
                    Console.Write(i + ",");  
                }  
                Console.WriteLine();  
            }  
            finally  
            {  
                Monitor.Exit(_object);  
            }  
        }  
  
        static void TestLock()  
        {  
              
            lock (_object)  
            {  
                Thread.Sleep(100);  
                Console.WriteLine(Environment.TickCount);  
            }  
        }  
  
        static void Main(string[] args)      
        {  
  
              
            Thread[] Threads = new Thread[3];  
            for (int i = 0; i < 3; i++)  
            {  
                Threads[i] = new Thread(new ThreadStart(PrintNumbers));  
                Threads[i].Name = "Child " + i;  
            }  
            foreach (Thread t in Threads)  
                t.Start();  
  
            Console.ReadLine();  
        }  
    }  
} 
```
