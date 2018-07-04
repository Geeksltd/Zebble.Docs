[app-orientation]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/device-environment/app-orientation.png

### DEVICE.SCREEN AND ORIENTATION (LANDSCAPE | PORTRAIT)

The Device.Screen object gives you access to all information and functionality of the screen.

To get the current device's width and height you can use:

```csharp
var width = View.Root.ActualWidth;
var height = View.Root.ActualHeight;
```

**Note:** On devices which have a logical buttons bar such as some Windows Phones, the above will give you only the usable size of the device as opposed to the hardware size.

#### App orientation

![app-orientation]

In general you may want your app to be:

- Always portrait (e.g.: Facebook app)
- Always landscape (e.g.: some games)
- Support either (e.g. Safari)

The default Zebble project template is configured to support both. But you can also change it to support only portrait or only landscape.

#### Configuring supported orientations

The following shows the configurations necessary for dynamic orientation (supporting both).

- **Android:** In MainActivity.cs file's Activity attribute:
  - set ScreenOrientation to Unspecified.
  - Set ConfigurationChanges to ConfigChanges.Orientation | ConfigChanges.ScreenSize
- **iOS:** In info.plist, set: 

```xml
<key>UISupportedInterfaceOrientations</key>
<array>
     <string>UIInterfaceOrientationPortrait</string>
     <string>UIInterfaceOrientationLandscapeLeft</string>
     <string>UIInterfaceOrientationLandscapeRight</string>
</array>
```

- **UWP:** In package.appxmanifest set 

```xml
<uap:InitialRotationPreference>
     <uap:Rotation Preference="portrait" />
     <uap:Rotation Preference="landscape" />
     <uap:Rotation Preference="landscapeFlipped" />
</uap:InitialRotationPreference>
```

#### Finding current orientation

If you app supports both portrait and landscape orientation, you can find the current orientation of the device for processing in your app using:

```csharp
if (Device.Screen.Orientation == DeviceOrientation.Portrate)
{
     // ...
}
else
{
    // Landscape logic...
}
```

You can also attach an event handler to detect changes in device orientation:

```csharp
...
{
     Device.Screen.OrientationChanged.Handle(OnOrientationChanged);
}

public Task OnOrientationChanged()
{
      var newOrientation = Device.Screen.Orientation;
      // ...
}
```