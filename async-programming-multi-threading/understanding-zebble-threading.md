### UNDERSTANDING ZEBBLE THREADING

You might know that in almost all native UI technologies, there is a concept of the UI Thread or the Main Thread, which is where the actual UI controls can be created or changed. Yet at the same time, to keep your app responsive you must minimise the amount of application code that runs on the UI Thread, so the operating system can use it to draw things on the screen and process user touches.

#### Zebble: your code run on the thread pool

In Zebble, by default, all your application code runs on the background thread - which means any thread from the thread pool. Your code can create and modify Zebble views in the virtual DOM (document object model) without worrying about the threading issues.

Behind the scene, the Zebble engine will monitor all the changes to the virtual DOM and automatically create or update the native UI on the UI Thread. So in essence, even though only the UI Thread is, in fact, handling the native UI objects, but this is not something for you to worry about in implementing the application code, creating UI objects, etc.

#### Explicitly running code on the UI thread

In rare cases, you might need to run your app code on the UI Thread. To achieve that use the following syntax. In such scenarios you should call:

```csharp
// Use the Run() method to invoke a method or lambda that returns a Task
Device.UIThread.Run(SomeTaskReturningMethod);

// Use the RunAction() method to invoke a void method or lambda.
Device.UIThread.RunAction( () =>  .... {ui change code}.... );
```

You'll need this for instance if you have to access the native view objects directly rather than through the Zebble objects. That's very rare and only used for certain advanced scenarios.

#### Explicitly running code on the thread pool

When your code is running in the UI thread, you may need to send a piece of code to run on a background thread for better responsiveness and to leverage the multiple processor cores on the device. In that case use the following syntax:

```csharp
Device.ThreadPool.Run(SomeTaskReturningMethod);
// Or
Device.ThreadPool.RunAction( () =>  .... {background code}.... );
```

#### Enforcing new background thread

Most of the time your code is running on a background thread and so you can run any code without causing any problem. When Device.ThreadPool.Run() or RunAction() is called, it will check to see if the currently running thread is already a non-UI thread, in which case it will run the action immediately on the same thread and return after it's done.

But in rare case you may want to ensure that a new thread is created to run an action and the call is returned immediately to execute the rest of your current code. A typical scenario is when using a precision timer. In those cases you can use the following method:

```csharp
Device.ThreadPool.RunOnNewThread( .... ); // Takes a task returning method or lambda
// Or:
Device.ThreadPool.RunActionOnNewThread( ... ); // Takes a void method or lambda
```

#### Scheduling UI code from UI thread!

When Run() or RunAction() are called on Device.UIThread they will check to see if the currently running thread is already the UI thread, in which case they will run the action immediately and return after it's done. But in the following rare case:

You are currently running on the UI thread
You want to schedule some action to run when the UI thread
But immediately return to run the rest of your code without waiting for that action
Then you can use another method called Post(), for example:

```csharp
// ... currently already running on the UI thread...
Device.UIThread.Post(() => ... {code to also run on the UI thread, but in the future when it's free}...);
// ... The rest of this code will immediately continue (also on the UI thread)...
```

#### Am I running on the UI Thread?

99% of the time your code should be running on the background thread, even when changing things on the UI. Zebble will automatically take care of  thread switching when reflecting your changes on the Zebble view objects on to the native UI objects. So you don't need to think about that.

But there may be rare cases when you have to explicitly run some code on the UI thread (such as advanced direct manipulation of native views). Even in those cases usually you should know what thread your code is running on. But in super advanced scenarios when that's not possible, you can use the following code to find out if your code code is running on the UI thread:

```csharp
if (Device.UIThread.IsRunning())
{
    //...
}
```