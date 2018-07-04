
### USE THE WINDOWS VERSION

When debugging the applications try to use the Windows version as much as possible.

- It's must faster to build and run
- The Visual Studio debugging tools are a lot more powerful
- You will have much faster feedback for debugging.

#### Beware: Debugging on iOS

There are cases when you can't use the Windows version for debugging and have to debug on the device. For example to test device motion. You can use Visual Studio for that purpose, but beware: 

- The Xamarin iOS debugging integration with Visual Studio can be shaky and unstable.
- It can frequently crash your Visual Studio.
- It's very slow to build, deploy to simulator or device, and run your application.
 
 

#### Tip: Testing styles for iOS and Android on Windows

Ctrl + Click on any element on the page to launch the inspection window. Then from the drop-down list at the top right corner, select a device to see the application updated for that device size and styles. Make sure to download the Android and iOS fonts for Windows. For example: http://www.fontex.org/download/Roboto.ttf