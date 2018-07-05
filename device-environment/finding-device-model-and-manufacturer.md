
### FINDING DEVICE MODEL AND MANUFACTURER

If you want information about the device where your app is currently running, you can use:

```csharp
if (Device.OS.HardwareModel.Contains("iPad"))
{
     // Something...
}
```

This will return "UNKOWN" if the device model is unavailable.