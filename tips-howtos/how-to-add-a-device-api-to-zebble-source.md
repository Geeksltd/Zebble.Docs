
### HOW TO ADD A DEVICE API TO ZEBBLE SOURCE?

The Zebble Device API provides a convenient and consistent way for developers to invoke native functions on all platforms. They are all invoked in the format of:

```xcharp
Device.Feature.Function(...);
```

In the above format **Feature** is a logical category for one or a number of specific native functions. For example for the Feature of **"Location"** we have a number of funcions such as *GetCurrentPosition(), StartTracking()*, etc.

If you want to add additional cross-platform functionality to Zebble, similar to the ones already implemented, then this articles explains how you can do it.

#### Step 1: Add a new Feature

To add a new api feature called **MyFeature**, you need to do the following:

In Core\Device\Device.cs file, add the following:

```csharp
public static readonly NativeImpl.DeviceMyFeature MyFeature = new NativeImpl.DeviceMyFeature();
```

Add a class named DeviceMyFeature.cs in the Zebble source under Core\Device in exactly the following pattern. 

```csharp
namespace Zebble.NativeImpl
{
    using ...;
    public partial class DeviceMyFeature
    {
        ...
    }
}
```

In this class add any necessary code that is shared between all 3 platforms.
In each of the Android, UWP and iOS projects in the Zebble source, and under the Device folder, add a partial class named DeviceMyFeature in the namespace of Zebble.NativeImpl.
Avoid using #if and #endif blocks for platform-specific code.

#### Step 2: Add a function to your feature

You can add one or more functions to your feature class. For each function (e.g. called MyFunction), you need to do the following:

In the shared DeviceMyFeature.cs file add a method with the following structure:

```csharp
public Task<TResult> MyFunction(args..., OnError errorAction = OnError.Alert)
{
      try
      {
            await DoMyFunction(args....);
            return true; // If your function is meant to return a value, remove this line and add "return" to the line above.
      }
      catch (Exception ex)
      {
             await errorAction.Apply(ex, "Invoking MyFunction failed....");
            return default(TResult);
      }             
}
```

If your method does not need to return anything (i.e. void), then return Task<bool>. This is important.
Depending on the nature of MyFunction, you might want to choose another default value for errorAction. Choose what makes sense as the default reaction scenario.
In each of the platform-specific partial classes, implement the DoMyFunction(...) method using the native API of that platform. In the case of errors, just let them throw. 

**Notes**

- Learn how you can [test your changes in the Zebble engine](https://github.com/Geeksltd/Zebble.Docs/blob/master/debugging/stepping-into-zebble-source.md).
- Make sure you install the [GCop Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=Paymon.GCop), and fix all its warnings for your code.
- Read the source code of some of the existing DeviceAPI implementations in the source to learn the coding style and ensure your implementation is compatible.