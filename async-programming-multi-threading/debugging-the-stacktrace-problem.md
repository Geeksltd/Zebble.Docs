
### DEBUGGING - THE STACKTRACE PROBLEM

In .NET development stack trace is maintained for each thread. The problem is that when you start a new task using any of the following methods:

```csharp
Task.Run(...)
Device.UIRuntime.RunAction(...)
Device.ThreadPool.RunAction(...)
Device.UIRuntime.Run(...)
...
```

Then the stack trace will be reset on the newly created task, and therefore you can't see the stack of the real caller who invoked this action on a different thread. So when an exception occurs, you can't really see what's going on as the stack will not tell you the whole story. This problem is not specific to Zebble but any kind of multi-threaded development.

#### Zebble's solution

In Zebble there is an innovation that helps you tackle this problem:

- In config.xml, set **MultiThread.Debugging** to **true**.
- Run the application to get the exception, or put a breakpoint anywhere you need.
- Use QuickWatch to observe **Zebble.UIRuntime.StackTrace** to see the full stack across multiple threads.
- Beware that this will considerably slow down your app. So use it only during development and don't forget to turn it off when demoing the app, doing performance tuning, or of course when releasing your app!

#### How does it do it?

When the flag is set to true, then every time you call any of the following, it will create a new instance of a **StackAwareSynchronizationContext** which holds the current stack, supports nesting and allows combining the full stack.

```csharp
Device.UIRuntime.RunAction(...)
Device.ThreadPool.RunAction(...)
Device.UIRuntime.Run(...)
...
```