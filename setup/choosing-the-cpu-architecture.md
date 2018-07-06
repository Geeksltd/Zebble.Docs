
### CHOOSING THE CPU ARCHITECTURE

Your Xamarin app can be deployed to a large array of mobile devices, each with a different CPU architecture, and SDK version. You define which SDK and CPU architecture you want to support, in your project’s properties and the build tasks will ensure the right binaries are then created. The settings you choose, will result in what device’s and OS’s your app can run on.

**During development, to make compilation faster and less error prone, select only the architectre that your emulator or device is using.**

Check this article for full details: https://xamarinhelp.com/choosing-cpu-architecture-sdk-version/

Here is a quick guide:

- ARMv6 – iPhone & iPhone 3G
- ARMv7 – iPhone 3GS, iPhone 4 & iPhone4S
- ARMv7s – iPhone 5 & iPhone 5C
- ARM64 – iPhone 5S & iPhone 6
- armeabi – Old devices
- armeabi-v7a – Samsung Galaxy S4
- arm64-v8a – Samsung Galaxy S7
- x86 – Emulators
- x86_64 – Emulators, Asus Zenphone 2