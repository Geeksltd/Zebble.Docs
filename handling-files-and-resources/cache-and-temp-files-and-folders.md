
### CACHE AND TEMP FILES AND FOLDERS

#### Cache folder

The Cache directory is a good place to store data files that can help your application run, but that can be easily re-created if required. The application should create and delete these files as needed and be able to re-create these files if necessary.

For instance, in case your application can't connect to the network, you might use the Caches directory to store data or files to provide a good offline experience. The application can save and retrieve this data quickly while waiting for network responses, but it doesn’t need to be backed up and can easily be recovered or re-created after a restore or version update.

The mobile operating systems may delete these files (under low storage situations), however they will not do so while the application is running. Also the contents of this directory are NOT backed up by iTunes, which means they will not be present if the user restores a device, and they may not be present after an updated version of your application is installed.

```csharp
var cacheFolder = Device.IO.Cache; // Returns a DirectoryInfo object

// For example:
var tempWorkingFolder =  Device.IO.Cache.GetFile(Guid.NewGuid().ToString() + ".txt");
```

#### Temp root folder

The following code returns the root temp folder in which to create temp files and folders which returns a DirectoryInfo object.

```csharp
// This returns ----> {Cache directory}\Temp
// Use it if you want to benefit from automatic clean up of the OS
var tempRoot = Device.IO.GetTempRoot(); 

// This returns ----> {Resources}\Temp
// Use it if you don't want the OS to delete anything and you want to handle the clean up yourself.
var tempRoot = Device.IO.GetTempRoot(globalCache: false); 
```
As you can see in the above examples, you can choose if you want the location of the Temp folder to be in the device's global cache directory (see above) or insdie the app's local directory like any other normal app file (i.e. equivalent to the Resources folder on the device).


#### Creating a temp directory

When you need to create a temporary folder in the application, use either of the following options. It will create a folder in the specified temp directory as a new GUID, so your temp directory is guaranteed to be unique.

```csharp
// This returns ----> {Cache directory}\Temp\{New Guid}
var myNewTempFolder = Device.IO.CreateTempDirectory();
Or alternatively:

// This returns ----> {Resources}\Temp\{New Guid}
var myNewTempFolder = Device.IO.CreateTempDirectory(globalCache: false);
```

#### Creating a temp file

Sometimes you need to create temporary files for implementing certain processes in your applications. To get a temp file use the following method:

```csharp
// This returns ----> {Cache directory}\Temp\{New Guid}.jpg
var file = Device.IO.CreateTempFile(".jpg");
```

This returns a temp file name, as a new guid, with the file extension that you specify. The location of that file will be in the temp directory which is in the device's global cache directory. This means that it can be cleaned by the OS when the device is running out of space.

Alternatively, if you don't want to use the global cache folder of the device operating system, you can use the following code:

```csharp
// This returns ----> {Resources}\Temp\{New Guid}.jpg
var file = Device.IO.CreateTempFile(".jpg", globalCache: false);
```

In this scenario the temp file will be created in the local Temp folder, which is itself in the Resources directory of the app, just like any other standard Zebble app file. If you use this option, then you need to ensure that you delete the temp files after you are done with them.