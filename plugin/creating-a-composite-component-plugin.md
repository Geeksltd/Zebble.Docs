[composite]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/plugin/composite.png

### CREATING A COMPOSITE COMPONENT / PLUGIN

You can create custom Zebble views which consist of other Zebble views, or which adds extended functionality to the current ones. In almost every project, you will create pages and modules by creating a class which is a sub-class of Stack, Canvas or any other View. In fact everytime you add a ZBL file to define a component, you are creating a composite view:

```xml
<z-Component z-type="..." z-base="..." >
      ....
</z-Component>
```

In most cases you only need that component in the same app project. But sometimes you may create a component that is useful across different projects, and you may want to turn that into a plug-in that any project can reference.

#### Creating a reusable composite component

In Visual Studio create a new project with the type **"Zebble Plugin - Composite View"**.

In the shared project, add a class to represent your component. It should inherit from Zebble.View or a sub-class of it such as Stack or Canvas.

```csharp
namespace Zebble.Plugin
{
   public partial class MyComponent : Zebble.Stack
   {
         …
   }
}
```

![composite]

Any code in the Shared project is logically a part of each one of the platform specific projects of UWP, Android and iOS. Those 3 are shell projects used to compile the same code (written in the Shared project) for the different platforms. So in terms of the logic of your component, normally all of your code will be written in the Shared project. You can of course add additional helper classes or sub-component to help you implement the primary Zebble plugin (named MyComponent in this example).

You can reference other assemblies or other Zebble plugins, in which case the assembly references should be added to the 3 platform specific projects.

#### Compiling & Distribution

All you need to do now is to compile the plugin solution. It will generate 3 DLLs (one for each platform) in the lib\ folder.  The name of the DLL files will be the name of your component followed by dot, following by the platform name. (e.g. Zebble.MyComponent.UWP.dll, Zebble.MyComponent.iOS.dll, ...).

You can reference these DLLs directly in any consuming Zebble project in the standard way, or package the plugin into a NuGet package and distribute via NuGet, which is the recommended approach. To create a NuGet package, simply complete the NuGet.Nuspec file already generated for you inside the Shared folder and submit to www.nuget.org!

#### Using it in the consuming applications

Once you add a reference to the plugin in your target Zebble project (either via NuGet or directly) then you can use it in your ZBL markup files or code behind files, just like any other standard or custom Zebble view type. For example:

```xml
<MyComponent Id="..." Property1="..." on-Event1="..." />
```