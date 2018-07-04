
### STEPPING INTO ZEBBLE SOURCE

#### Why step into Zebble source?

Sometimes you may need to step into the Zebble source code. For example when:

- You want to build a new feature in the Zebble framework.
- Step into the Zebble source code for advanced debugging of your app - to achieve more visibility on what's going on, and to find the root cause of the bugs in your app.

#### Compile Zebble locally

Normally when your application is referencing the Zebble dll using NuGet, Visual Studio is unable to step into its code. To solve this problem do the following:

- Copy the Zebble source onto your machine at **C:\Projects\Zebble**
- Compile it so you get the Zebble DLLs and PDB files in **C:\Projects\Zebble\Lib folder**.

#### Configure your app

The next step is to make your app use the locally compiled Zebble code instead of the nuget package. For each platform:

- Uninstall the Zebble NuGet package from your app. 
- Physically delete all **{SolutionFolder}/packages/Zebble.xxx** folders from your file system.
- Reference the locally compiled DLL in the sample app from the local Zebble **lib** folder
If you want to change Zebble.exe, then copy Zebble.exe from your local lib folder to {MyApp}\Run\Android

Now you can open any specific Zebble source file inside your app's Visual Studio instance and put break-points where you need.

```
Alternatively you can automatically do all of this by running the following command:

C:\Projects\MyApp\Run\Android\> Zebble.exe debug-zebble
```

#### Important note

When you step into the Zebble source for debugging, there can be different outcomes:

- It may shed light on an error in your own app code, resources, or network setting, etc.
- You might also find a bug in the Zebble itself. In this case:
    - We suggest that you try to find a fix that you can use in your project, and ideally submit to us (pull request) to include in the next version of Zebble.
    - If you can't find a solution yourself, feel free to report the bug for our team to fix.