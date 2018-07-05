[permission1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/device-environment/permission1.png
[permission2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/device-environment/permission2.png

### PERMISSIONS

You can use the **Device.Permissions** object to check for checking or requesting access to the following device elements.

#### Available on all platforms:

![permission1]

- Albums (for photo or video gallery)
- Camera
- Microphone (for recording audio, or using speech-to-text)
- BodyMotions (for accessing the user's current activity such as walking, running, etc)
- Location
- Contacts
- Calendar
- Reminders
- PhoneCall
- SendSms
- Speech

**Example**

The following checks if a permission is already granted. But it does not request the user for it:

```csharp
if (await Device.Permissions.Check(DevicePermission.Microphone) == PermissionResult.Granted)
{
      ...
}
```

Which can also be reached with the following shortcut extension method:

```csharp
if (await DevicePermission.Microphone.IsGranted())
{
    ...
}
```

Sometimes you don't know if the permission is already granted. If it's not granted, you want to request the user for permission. But if it's already granted, you don't want to annoy the user by asking again. The Request() method takes care of both scenarios.

```csharp
if (await Device.Permissions.Request(DevicePermission.Microphone) == PermissionRequest.Granted)
{
    ...
}

// OR THE SHORTCUT WAY:
if (await DevicePermission.Microphone.Request() == PermissionRequest.Granted)
{
    ....
}
```
 
If you want to access any of the device sensitive information and hardware (such as user location, camera, etc) you should ensure you have access before you do that.

**Example:**

```csharp
async Task MyButtonTapped()
{
    if (await DevicePermission.Camera.Request() != PermissionResult.Granted) return;
    // ...
}
```

Alternatively in M# settings of the Button (or menu item) set **"Required Permissions"** to **"Camera"** and the above code will be generated.

 
#### Use Check() or Request()?

![permission2]

When the app feature using the permission needs to be subtle and not annoy the user with a permission dialog, then use **Check()**. This is usually relevant to optional features.

But if the feature is critical and you don't mind disturbing the user and ask for permission, use **Request()**.

#### Android Only Permissions
The following permissions are also available for processing on Android only. 

ReadPhoneState, ReadCallLog, WriteCallLog, AddVoicemail, UseSip, ProcessOutgoingCalls, ReceiveSms, ReadSms, ReceiveWapPush, ReceiveMms
For using these, your relevant app code should be wrapped in ANDROID symbol definition only. For example:

```csharp
...
#if ANDROID
    if (await DevicePermission.WriteCallLog.Request() == PermissionRequest.Granted) { ...}
#endif
...
```

### iOS info.plist

Starting in iOS 10, nearly all APIs that require requesting authorization require a new key value pair to describe their usage in the **Info.plist**. [Learn more](https://blog.xamarin.com/new-ios-10-privacy-permission-settings/).