
### TIMER (INTERVAL / SCHEDULED RUNNING)

Sometimes you need to run some action regularly in certain time intervals. To achieve that in Zebble you can use the Timer class using the following:

Let's say you have an method like below and you want it to run every second:

```csharp
async Task DoSomething()
{
     ...
     await Alert.Toast("Hello! Time is " + DateTime.Now);
}
```

To make it run every second you should create a timer for it using the following pattern:

```csharp
...
using Zebble.Services;

...

new Timer(DoSomething, TimeSpan.FromSeconds(1), Timer.WaitingOption.Parallel).Start();
```

#### WaitingOption

The last parameter of the construction is an enum value of type Waiting option. You can choose from either of the following:

- **Parallel:** It means to run the action on a new thread exactly at the specified intervals, irrespective of how long it takes.
- **WaitForCompletion:** It means to run the action and wait for its completion, then wait for the interval duration. 