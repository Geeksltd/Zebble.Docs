[windows]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/introduction/windows.png "Zebble-windows"
[android]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/introduction/android.png "Zebble-windows"
[ios]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/introduction/ios.png "Zebble-windows"

### INSTALLING - INTRODUCTION
Zebble supports 3 platforms, but they are all optional. This means that you can have a project that uses only one platform, two or all. To support each one of the platforms, your development environment needs to have certain components installed.

#### Platform Target: Windows

![windows]

To build a Universal Windows Platform app with Zebble, you will need:

- Windows 10 operating system
- Visual Studio 2015, update 3 or Visual Studio 2017 (recommended)
- The latest [Windows Standalone SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) (version 10.0.14393.0) 
     - Have any problems with UWP ? Try [this](http://stackoverflow.com/questions/32408480/how-to-install-windows-10-universal-development-tools-in-vs-2015) and [this](http://stackoverflow.com/questions/31704614/universal-apps-template-missing-in-visual-studio-2015-community).
- .NET Core 1.1 ([here](https://www.microsoft.com/net/download/core))
- Windows 10 mobile emulators. [How?](http://stackoverflow.com/questions/31209172/cant-find-windows-10-emulators-in-visual-studio-2015)
- Faced any problems? [Try this](http://stackoverflow.com/search?q=zebble).
 

#### Platform Target: Android

![android]

To build an Android app with Zebble, you will need:

Any Windows operating system
Visual Studio 2015, update 3
Xamarin for Visual Studio
Android SDKs, Emulators, etc (see the link)
 

#### Platform Target: iOS

![ios]

To build an iOS app with Zebble, you will need:

Any Windows operating system
Visual Studio 2015, update 3
Xamarin for Visual Studio
A Mac with proper components installed (see the link)
### Development Environment:
|                             |  Mac OS                 | Windows              |
| :-----------                | :-----------            | :------------        |
| **Development Environment** | VISUAL STUDIO FOR MAC   | VISUAL STUDIO        |
| **Xamarin.iOS**             | YES                     | YES (with Mac computer) |
| **Xamarin.Android**         | YES                     | YES                   |
| **Xamarin.Forms**           | iOS & Android only <br> (macOS in preview) | Android, Windows/UWP <br> (iOS with Mac computer) |
| **Xamarin.Mac**             | YES                     | Open project & compile only |

For more information: https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install