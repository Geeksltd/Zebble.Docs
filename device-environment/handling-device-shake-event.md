
### HANDLING DEVICE SHAKE EVENT

If you want your app to respond to the user shaking the phone, then you need to follow these instructions:

#### In Config.XML, enable shaking detection:

```xml
<Device.System.DetectShaking>true</Device.System.DetectShaking>
```

On the Zebble page or module that should respond to Shaking, add an event handler in the OnInitializing event:

```csharp
public override async Task OnInitializing()
{
        await base.OnInitializing();
        // ....
        Device.Accelerometer.DeviceShaken.Handle(OnDeviceShaken);        
}
```

Add the event handler:

```csharp
Task OnDeviceShaken()
{
    return Alert.Show("TADA! You device was shaken!");
}
```

Remove the handler when your page or module is disposed:

```csharp
public override void Dispose()
{
    Device.Accelerometer.DeviceShaken.RemoveHandler(OnDeviceShaken);
    base.Dispose();
}
```

#### Testing on Windows

To test the shake functionality on Windows (dev time) launch the inspector by pressing the Ctrl + Click on any element.

The on the top bar, click on the Shake icon.