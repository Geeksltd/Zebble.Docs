
### FASTEST WAY TO UPDATE YOUR NUGET PACKAGE

Using the traditional method to update nuget was painful as you have to:

- Load Adroid, UWP and iOS projects
- Launch Visual Studio Nuget manager
- Find the package, tick all boxes and click Install
- Wait for a long time for things to be downloaded.
- Unload the projects again and load the one you cared about.

More importantly you had to wait for several minutes for a fresh release to be indexed and available.

**A better way!**

You can just run the Zebble.exe command with the following parameter:

> C:\Projects\....\Run\Android> Zebble.exe update-nuget

It will do everything for you!