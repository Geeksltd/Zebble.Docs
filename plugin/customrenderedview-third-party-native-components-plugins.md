[view1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/plugin/view1.png

### CUSTOMRENDEREDVIEW: THIRD-PARTY NATIVE COMPONENTS / PLUGINS

Sometimes you need to add a third party or custom native component to your app.

In such cases you may have found a different component for iOS, Android and Windows, which all do the same thing that you want, but with different APIs.
Or you might only have the Android and iOS plugins, but still need to have a simulated one for UWP to enable dev and testing.
CustomRenderedView is a special view type in Zebble allowing you to embed such components into a Zebble application. 

#### Step 1: Create a new Zebble Plugin project

![view1]

Although you don't have to, it's strongly recommended packaging the third party or custom component into a Zebble Plugin, so you can reuse it in multiple projects. Also, this gives you the ability to offer the plugin to the community via github or NuGet.

First, create a new project in Visual Studio using the template: **Zebble Plugin - Component Adapter**.

It will then create a new Visual Studio solution for you containing 4 projects:

- Shared
- Android
- iOS
- UWP
 

 
#### Step 2: Creating Native Adapter(s)

In the Shared project, you will have a Zebble view class to represent an instance of your component using the following pattern. This class will be in the Shared project, available to all 3 platforms:

```csharp
namespace Zebble.Plugin
{
    public class MyComponent : View, IRenderedBy<Renderer.MyComponentRenderer>
    {
           ...
    }
}
```

This class is a Zebble compatible abstraction of the third party component. It inherits from a Zebble view class named CustomRenderedView<T> which itself inherits from the base Zebble View class. This way your component class also becomes a Zebble view.

The role of this class is to provide a cross platform abstraction, or concept, of the component. It's not tied to any platform-specific implementation of that concept. Other Zebble projects can instantiate it and use it just like any other Zebble view object.

Inside this class, you should define all the properties, methods and events that your component concept can provide. Note that these are high-level, and do not contain any platform-specific implementation details, but you can include any business logic related to the component concept. The project template will give you an example code for each of these. So just follow that logic.

#### Step 3: Reference the native (3rd party) components

Of course at some point, your component concept needs to actually be rendered and run in each platform. Usually you will already have a third party Xamarin iOS, Xamarin Android or UWP component that provides the implementation and you need to make them work with the Zebble abstraction.

For example the [Xamarin website lists tens of third party components](https://components.xamarin.com/). There are also [thousands of them on NuGet](https://www.nuget.org/packages?q=xamarin). Each one of these may support all 3 platforms (UWP, Android, iOS) or just one or two of them. 

All you need to do is to add a NuGet referece to package that provides the native platform-specific implementation.

**Note 1**: Sometimes a third party single plugin will support some but not all platforms (UWP, Android, iOS). In that case you can use it for the platforms that it supports, and find another plugin for the remaining platforms. The important thing is that logically they all provide all the functionality required in your Zebble component abstraction, although their APIs can differ. As you see in the next section, you have the flexibility to map the functionality of your Zebble component concept to each native platform separately to bring a unified API for the end product.

**Note 2**: You do not need to add any reference to the Shared project in Visual Studio. That is a special project type used solely for code sharing. Any file in the shared project is deemed to be a part of each one of the UWP, Android and iOS projects ([learn more](http://stackoverflow.com/questions/30634753/what-is-the-difference-between-a-shared-project-and-a-class-library-in-visual-st)).

#### Step 4: Creating native renderers

Each of the 3 platform specific projects in your solution (UWP, iOS, Android) will have a xxxRenderer class with the following template. There, effectively you need to create a one-to-one mapping between the Zebble abstraction (created in step 2) and the real native implementation (i.e. the third party component).

```chsrp
public class MyComponentRenderer : ICustomRenderer
{
      MyComponent View;
      TheNativeType Result;

      public Task<{BASE NATIVE VIEW TYPE}> Render(object view)
      {
          View = (MyComponent)view;
          Result = new TheNativeType();

          // TODO: Map the properties, events, etc.

          return Result;
      }

      public void Dispose() => Result.Dispose();
}
```

You should replace {BASE NATIVE VIEW TYPE} with the correct value for each platform:

- UWP -> Windows.UI.Xaml.FrameworkElement
- Android -> Android.Views.View
- iOS -> UIKit.UIView

#### Step 5: Compile (or package!)

All you need to do now is to compile the plugin solution. It will generate 3 DLLs (one for each platform) in the lib\ folder.  The name of the DLL files will be the name of your component followed by dot, following by the platform name. (e.g. MyComponent.UWP.dll, MyComponent.iOS.dll, ...).

You can reference these DLLs directly in any consuming Zebble project in the standard way, or package the plugin into a NuGet package and distribute via NuGet, which is the recommended approach. To create a NuGet package, simply complete the nuspec file already generated for you inside the Shared folder and submit to www.nuget.org!

#### Using it in the consuming applications

Once you add a reference to the plugin in your target Zebble project (either via NuGet or directly) then you can use it in your ZBL markup files or code behind files, just like any other standard or custom Zebble view type. For example:

```xml
<Zebble.Plugin.MyComponent Id="..." Property1="..." on-Event1="..." />
```