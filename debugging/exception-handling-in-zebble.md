
### EXCEPTION HANDLING IN ZEBBLE

In mobile app development, things can go wrong easily. Especially when using the device APIs, Web APIs and network features, there is always a chance for network being down, permission not being granted, etc. Yet, your app should never crash, which means you should handle exceptions gracefully.

#### OnError enum

There is an enum in Zebble called OnError which defines your preferred reaction in cases of any unhandled exceptions when calling a method. It helps keep your code simple and clean while keeping the user informed when necessary. The options in this enum are:

- **Ignore:** It means the error should be silenced and ignored (internally using a try-catch block)
- **Throw:** It means the exception should be thrown. Use this when you want to handle exceptions manually in your code.
- **Toast:** It means the error message should be displayed to the user using a gentle toast message.
- **Alert:** It means the error message should be displayed in an alert, forcing the user to click OK to get rid of it.
#### Where to use it?

Several APIs in Zebble support an optional parameter of the type OnError. The following example is to turn on the device torch (lamp) by providing the error handling strategy parameter:

```csharp
// The default value of the error action TurnOn() is Toast.
// This means the app will not crash, yet the user will be informed that turning on the lamp failed.
await Device.Torch.TurnOn();
```

But if you want to handle the error case yourself, then you can do:

```csharp
try
{
     await Device.Torch.TurnOn(OnError.Throw);
}
catch (ex)
{
     // TODO: Handle it differently
}
```

#### Tip: Supporting OnError in your own code

When creating your own reusable components and APIs you might want to support OnError to enhance the usability of your component. The following explains how you can implement it:

- Provide an optional parameter of type OnError named *errorAction*.
- Ideally, provide the default value of the errorAction (Toast is recommended).
- Wrap your method body in a try-catch block.
   - In the catch block, invoke the Apply() extension method on the errorAction and pass the caught exception to it.
   - If your method should return something, return the default value (e.g. null) which is used in cases other than Throw.