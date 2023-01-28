# What is the difference between Task.Run() and Task.Factory.StartNew()

Both **Task.Run()** and **Task.Factory.StartNew()** are used to start a new task in C#, but they have some differences in their usage and behavior.

**Task.Run()** is a simpler way to start a new task, and is used for fire-and-forget scenarios, where you don't need to wait for the task to complete or get its results. It creates a new task and starts it immediately.

**Task.Factory.StartNew()** is more powerful, and provides more options for configuring the task, such as setting a task scheduler, passing a cancellation token, and getting the task's result. It also allows you to create and configure a task before starting it.

Additionally, Task.Run() uses TaskScheduler.Default to schedule the task, while Task.Factory.StartNew() allows you to specify a custom scheduler.

To summarise, if you want simple fire-and-forget task execution use Task.Run() and if you want more control over task execution use Task.Factory.StartNew().
