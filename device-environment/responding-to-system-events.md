
### RESPONDING TO SYSTEM EVENTS

There are a number of system-level events that may be raised automatically from time to time.

#### Activated

This is called when the application is launched and every time the app returns to the foreground. You can restart any tasks that were paused (or not yet started) while the application was inactive. If the application was previously in the background, optionally refresh the user interface.

```csharp
Device.App.Activated.Handle( ... );
```

#### App.ReceivedMemoryWarning event

This event is raised by the operating system when your application appears to be increasing its use of memory too quickly, or if it has over-time occupied a lot of memory. Neither one has exact definitions and limits specified.

Depending on your app's functionality, when this event happens, you may be able to lower your use of RAM, e.g. by releasing resources that can be loaded again later when needed.

```csharp
Device.App.ReceivedMemoryWarning += ... ;
```

#### App.WentIntoBackground event

This event is raised when your app is going into the background, e.g. by pressing the home button on the device. Use this method to release shared resources, save user data, invalidate timers and store the application state.

```csharp
Device.App.WentIntoBackground += ...;
```

#### App.Closing event

This event is raised when your app is being closed. Similar to WentIntoBackground, you can use this method to release shared resources, save user data, invalidate timers and store the application state. 

```csharp
Device.App.Closing += ...;
```

**Note:** Unlike other events in Zebble, the above 3 events are normal events as opposed to AsyncEvent. They always run on the UI thread and must complete their job quickly.