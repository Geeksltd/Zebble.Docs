[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/12-1.png

### MANAGING FILES & RESOURCES

In this lesson, you will learn about the fundamental problems in managing files and resources in cross-platform mobile development such as distribution, synchronization, duplication and address consistency.

You will also learn about the Zebble innovation to bring a consistent, simplified and clean API for managing files and folders with no compromise in flexibility.

[Download this video directly](https://drive.google.com/file/d/0B3EED8dgociyc2xqamtGQm5QdjA/view?usp=sharing)

[![INTRODUCTION TO ZEBBLE](https://github.com/Geeksltd/Zebble.Docs/blob/master/assets/tutorials/1.png?raw=true)](https://youtu.be/rR7VaFBz8yA)

----------------------------------------

#### Background: Understanding file problem in Mobile (pre-Zebble)

In all mobile platforms other than Zebble the process of transferring files from a mobile app source code to the run-time (simulator or device) for installation and testing is very difficult. In general you can either include the files as **embedded resources** or as **bundle contents**. But both options are problematic:

- **Content Files** don't get uploaded to the runtime **each time you compile and test**. You have to go through a lengthy reinstallation process to make it work, and have to apply special settings for each file in your Visual Studio project. It's inconvenient, error-prone and unreliable, leading to hard-to-debug problems. Specially when you update or replace a file, it gets really tricky to consistently cascade the change runtime.

- **Embedded Resources** are easier to transfer to the device or simulator consistently, but they come with their own problems. Firstly the API to retrieve them is awkward, error-prone and ugly. Secondly you can't at runtime modify such files, delete or update them. So it's not possible to use it for many scenarios.

#### Zebble's File Management System

Zebble introduces a clever new model to solve the mobile file problem.

![1]

You include all files in a directory in your source in App.UI/Resources.

Upon compilation, a pre-build action will run **Zebble.exe** which will:<br>
- Ensure all files in the above directory are added as Embedded Resource.
- Read the actual binary content of all the files and create a total Hash string, which is considered the "ResourceVersion".
- The calculated ResourceVersion will be hard-coded in the Startup.cs class.
- Upon start-up of the application it will automatically goes through the Embedded Resources to find each file and then copies it onto the App's local runtime directory if necessary.
   - This will happen only if the application is installed for the first time, or if anything in the App.UI/Resources is changed.
So in practice when ever you change any files in the Resources folder, it will automatically be installed when it runs.
- Unlike traditoinal embedded resources, in your app code, you can create new files or modify/delete existing ones as if they were simple files in the App folder.

#### File Access API

Although the files in your Visual Studio source will be Embedded Resources, but you can then deal with them in your app code simply as files and not embedded resources using the familior System.IO API in .NET such as FileInfo or DirectoryInfo.

The physical location of the files will be different in every platform. So you cannot reference any file with its absolute path. To find the actual path of any file or directory, use the following:

```csharp
FileInfo myFile = Device.IO.File(relativePath);
DirectoryInfo myDirectory = Device.IO.Directory(relativePath);
```

**Example:**

```csharp
// This returns the actual folder on the device, corresponding to the [App.UI]\Resources\Images folder in your Visual Studio source.
var imagesDirectory = Device.IO.Directory("Images");

// This returns the actual file on the device, corresponding to the [App.UI]\Resources\Images\Something.png in your Visual Studio source.
var myFile = Device.IO.File("Images/Something.png");
```

#### Referencing files in View objects

Some views such as ImageView or Video have a Path property to specify their source. The value that you specify for them should be simply the relative path of the file inside the Resources folder. For example:

```xml
<ImageView Path="Images/Something.png" />
```

However, they also support an absolute file path. This is handy becuase sometimes your source file may be outside of the Resources directory, such as a file in the device's Cache folder.

For example, if you have a FileInfo object in your code, and you want to set as as the source of an ImageView, you don't have to convert it back to the relative path format. Instead simply use the absolute form. For example:

```csharp
FileInfo  myFile = ... ; // E.g. dynamically created, or downloaded, or retrieved from the cache folder, etc.
myImageView.Path = myFile.FullName; // This is the absolute path, but it's fine.
```