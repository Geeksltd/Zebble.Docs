### PERMISSIONS DECLARATION (MANIFEST FILES)

Checking permissions at run-time is not enough.

Your application should also declaratively define what permissions it is going to need, which is verified by the App Store approval teams at Apple, Google and Microsoft. 

So for each device feature listed in the permissions, you must also add appropriate settings to the manifest files of each native project in Visual Studio.

#### Android

for **Android**: In Visual Studio click on the project's **Properties > Android Manifest**.

See https://developer.android.com/reference/android/Manifest.permission.html for the full details

#### Windows (UWP)

These should be added to the file **Package.appmanifest > Capabilities**

#### iOS

These should be added to the **Info.plist** file. 

As of iOS 10, for each permission for iOS, you should provide a sentence to explain WHY your app functionality depends on the requested information. Without writing these declarations and justifications, your app will be rejected.

https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html