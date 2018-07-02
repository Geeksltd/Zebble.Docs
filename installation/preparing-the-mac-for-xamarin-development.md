[connecting]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-the-mac-for-xamarin-development/connecting.png "Zebble-MAC"
[iossetting]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-the-mac-for-xamarin-development/iossetting.png "Zebble-MAC"
[iostoolbar]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-the-mac-for-xamarin-development/iostoolbar.png "Zebble-MAC"
[outputoptions]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-the-mac-for-xamarin-development/outputoptions.png "Zebble-MAC"
[toolbaroverview]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-the-mac-for-xamarin-development/toolbaroverview.png "Zebble-MAC"

### PREPARING THE MAC FOR XAMARIN DEVELOPMENT

#### Requirements & Installation

There are a few requirements that must be adhered to when developing for iOS in Visual Studio. As briefly mentioned in the overview, a Mac is required to compile IPA files, and applications cannot be deployed to a device without Apple’s certificates and code-signing tools. Also, the iOS simulator can be used **only** on a Mac.

There are a number of configuration options available, so you can decide which works best for your development needs. These are listed below:

- Use a Mac as your main development Machine and run a Windows Virtual Machine with Visual Studio installed. We recommend using VM software such as [Parallels](http://www.parallels.com/products/desktop/) or [VMWare](http://www.vmware.com/products/fusion/) .
- Use a Mac just as a Build Host. In this scenario it would be simply connected to the same network as a Windows machine with the [necessary](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Configuring_The_Mac) tools installed.

In either case, you should follow these steps:

- [Install the Xamarin.iOS tools on your Mac host and activate your license](https://developer.xamarin.com/guides/ios/getting_started/installation/mac/)
- [Configure your Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Configuring_The_Mac)
- [Install Xamarin tools on Windows](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Windows_Installation)

To develop with Xamarin in Visual Studio, you must be using **at least** Visual Studio 2013 Professional or higher. Xamarin will **not work** with Express Editions of Visual Studio, as they do not support add-ins.

 

#### Visual Studio Features for iOS

This section introduces the new Visual Studio features that support Xamarin iOS development. These include:

- Visual Studio Toolbar
- iOS and WatchOS applications and extensions
- iOS Designer
- iOS Project Properties

#### Connecting to the Mac

You can connect to your Mac build host either via the icon on the Visual Studio toolbar (providing an iOS application is open):

![connecting]

Or by browsing to **Tools > Options** in Visual Studio and selecting **Xamarin > iOS Settings**:

You can change the Mac Build Host by clicking the **Find Xamarin Mac Agent** button. The following screen is displayed to update the Mac Build Host:

![iossetting]

#### Visual Studio Toolbar Overview

Xamarin iOS for Visual Studio adds items to the Standard toolbar and to the new iOS toolbar. The functions of these toolbars are explained below.

Standard Toolbar

The controls relevant to Xamarin iOS development are circled in red:

 
![toolbaroverview]


- **Start** - Starts debugging or running the application on the selected platform. There must be a connected Mac (see the status indicator in the iOS toolbar).
- **Solution Configurations** – Allows you to select the configuration to use (e.g., Debug, Release).
- **Solution Platforms** - Allows you to select iPhone or iPhoneSimulator for deployment.

##### iOS Toolbar


The iOS Toolbar in Visual Studio looks similar in each version of Visual Studio. These are all shown below:

![iostoolbar]

Each item is explained below:

- **Mac Agent/Connection Manager** – Displays the Xamarin Mac Agent dialog box. This icon will appear orange when connecting, and green when connected.
- **Show iOS Simulator** – Brings the iOS Simulator window to the front on the Mac.
- **Show IPA File on Build Server** – Opens Finder on the Mac to the location of the application’s IPA output file.

#### iOS Output Options

**Output Window**

There are options in the Output pane that you can view to discover build, deployment, and connection messages and errors.

The screenshot below shows the available output windows, which may differ depending on your project type:

![outputoptions]

You can find more information here: 

https://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/