[solution]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/zebble-designer-uwp/solution.png "Zebble-Intro"
[incpection]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/zebble-designer-uwp/incpection.png "Zebble-Intro"
[incpection1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/zebble-designer-uwp/incpection1.png "Zebble-Intro"
[incpection2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/zebble-designer-uwp/incpection2.png "Zebble-Intro"
[incpection3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/zebble-designer-uwp/incpection3.png "Zebble-Intro"


### ZEBBLE DESIGNER (UWP)

Under the RUN folder you will see a project named UWP which contains a Windows runtime, allowing you to run the application instantaneously without waiting for device compilations (that typically take minutes each time).



During the development phase of the project, you will primarily be using the Windows Universal version as it's very quick, but also gives you the full debugging features of .NET, so it's perfect to get your application specific logic right.

 
![solution]
  

#### Inspection Tool
You can CTRL + Click on any item to launch the inspection window. That allows you to see the current page's tree of views to see how the current page is composed of its parts.

You can also change the property values and see their effect in real time. This can be a very helpful utility for debugging visual errors and to find fixes. (Although once you find a fix, you should still apply it in the main code yourself).

Press Ctrl+Click on Type label:


![incpection]

![incpection1]


Click on the Page object:


![incpection2]
 

**Note:**

In new version of Zebble VSIX plugin and Nuget packages, inspector will show you a Visual Studio icon for any object in the tree of which source is in your own app.

When you click that icon, the file will open in Visual Studio automatically, so you don't have to search to find it.

![incpection3]