[vsinterface]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/installing-for-android/visualstudiointerface.png "Zebble-Android"
[outputpage]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/installing-for-android/outputpage.png "Zebble-Android"

### INSTALLING FOR ANDROID

#### Installation

**Automatic Installation**

The Xamarin.Android installer will automatically detect, download, and install any components required (JDK, JRE , ANDROID SDK, NDK) for completing the installation.Fill the form and download Xamarin Installer [here](https://www.xamarin.com/download) and follow the steps.

After installing the SDK, some additional components need to be installed via the Android SDK Manager. Check to install at least:

- Android SDK Tools
- Android SDK Platform-Tools
- Android SDK Build-Tools
    - One (or more) Android Platforms (such as 4.4 / API 19 in the screenshot below).
 
**Manual Installation**

You can find all required files in **\\server\@Software\Android for Xamarin** <br>
**JDK and JRE:** Install them on your machine. <br>
**Android SDK:** Unzip andriod sdk to your **C:\Android\AndroidSDK** folder <br>
**Android NDK:** Unzip android ndk to your **C:\Android\AndroidNDK** folder <br>

#### Configuration

1. To configure the Visual Studio tools, navigate to **Tools > Options > Xamarin > Android Settings** and set all location paths for JDK , SDK and NDK.

For Example :

- JDK: C:\Program Files (x86)\Java\jdk1.7.0_55
- SDK: C:\Android\AndroidSDK\android-sdk
- NDK: C:\Android\AndroidNDK\android-ndk-r10e\
2. Make sure your android path is registered in your machine Environment Variables.

  Right click on My computer > Properties > Advanced System setting > Environment Variables on user variable, in the value of PATH key, you should have this **"C:\Android\AndroidSDK\android-sdk\tools;C:\Android\AndroidSDK\android-sdk\platform-tools;"**
 

3. In Visual Studio, Options > Debugging > General: Check "Enable just my code". 

#### Running on the simulator 

For running and testing your application you need to use one of Android Emulators. There are many different emulators available for Xamarin Android, but it is recommended to use Visual Studio Android Emulator for testing Zebble Apps. Visual Studio Android Emulator is a built-in Android player which runs under **Hyper-V**. So your computer must meet the requirements to run Hyper-V. Hyper-V requires a 64-bit version of Windows 10.


> Start **cmd.exe** with Admin rights and type  **“bcdedit /set hypervisorlaunchtype auto”**. Then restart your computer.


You can find the complete instructions for installing the emulator here. [Here](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/visual-studio-android-emulator/) is a summary, but if you run into any trouble make sure to read the full instructions:

- Close all Visual Studio instances
- In Start menu search for **"Visual Studio Emulator for Android"**.
    - If you don't have it, you can install the [VS Android Emulator](https://www.visualstudio.com/vs/msft-android-emulator/) 
      Otherwise run it.
- In the list of device profiles, download and install a **Marshmallow (6.00) XXXHDPI** Phone (e.g. 5.7" or 5.5").
- Launch the simulator and ensure it boots up and unlocked.
- Download the [Google Apps services](http://www.devfiles.co/download/m4Er5IlQ/gapps-600-base-20151016-1-signed.zip)
- Drag and drop the downloaded zip file into the running emulator. 

Make sure that you have selected needed architecture for running your apps on the Emulator in *Project Properties > Android Options > Advanced section, under Supported Architecture*. 

**Note:** If Android emulator opens successfully, but the deployment does not start, Check your windows registery **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools** path.

#### Running on the device

You should configure your device to allow debug (testing) mode: 

https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/

**Visual Studio interface :**

![vsinterface]

**Output page:**

![outputpage]