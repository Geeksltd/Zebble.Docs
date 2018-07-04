[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/debugging/1.png

### LOGGING MESSAGES FOR DEBUGGING

Normally in .NET you can use Console.WriteLine or Debug.WriteLine to send messages to Visual Studio output window from the application. In Zebble, instead of that try to use the following, which adds some advantages:

```csharp
Device.Log.Message("My message");
Device.Log.Warning("My warning message"); 
Device.Log.Error("My error message"); 
Device.Log.Error(myException); // Full exception data will be logged
```

#### Where can you see the log?

The log messages can be seen in Visual Studio's output window. It's strongly recommended that you install the [VSColorOutput plugin for Visual Studio](https://www.visualstudiogallery.msdn.microsoft.com/f4d9c2b5-d6d7-4543-a7a5-2d7ebabc2496) so that you can more easily distinguish between the messages that you log and the system logs and other noise. When you install this plugin, your output will look something like:

![1]

#### Logging variables

Normally when debugging your apps, you can use the standard Visual Studio debugging features to inspect variable values. But there are cases when that approach doesn't help you find the root cause of the issues. A common scenario is when a method is called many times for different things, and manually inspecting it every time and keeping track is not practical. In such cases a good practice is to log the variables and values that you care about so you can then look into the full log and analyse it.

To facilitate this there is a handy method in the Zebble log class which you can use to log multiple variables easily:

```csharp
Device.Log.Values(new { firstVariable, secondVariable, someObject.SomeProperty, ....});
```

Instead of passing the variables directly to this method, you need to provide one anonymous object where each property is a variable that you want to log. This clever technique allows the log method to know the names of the variables and log them next to the values!

```
{
    firstVariable -75
    secondVariable -16.65
    SomeProperty Hello world
    ...
}
```