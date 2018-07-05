[js1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/plugin/js1.png
[js2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/plugin/js2.png


### CREATING A ZEBBLE COMPONENT USING HTML AND JAVASCRIPT

![js1]

In Zebble it's very easy to bring your web development skills to build mobile components that are used in the middle of your native Xamarin app. Although a native Xamarin based app such as Zebble provides a better user experience compared to Hybrid apps, but it doesn't mean that Html and Javascript have no place. On the contrary, for certain UI elements web technologies are a perfect fit.

#### When and why use Html/Javascript?

The rule of thumb is, if for the particular page of your app, a delay of 200-300 milliseconds (or even 1 second for the first time) is acceptable, then you can benefit from the vast productivity gains and reusability options available in the web stack.

This means that HTML/Javascript would be a bad choice for things that the user will interact with a lot (menu, overall navigation, text buttons, ...) as the slight lag would negatively impact the user's experience.

But the are cases where you need a complex piece of UI such as displaying dashboard charts, a signature pad, a game, etc. In such scenarios, the initial lag of 200-300ms is psychologically very acceptable by the users, because it's a small overhead compared to the time they will spend using that component.

#### Creating a HTML based Zebble plugin

![js2]

1. In Visual Studio create a new project with the type **"Zebble Plugin - Composite View"** as explained [here]().

2. Under the Shared project, add a folder named Asset and copy all your web files in there such as Html, Javascript, Css and Image files.

3. Set the build action of all files inside the Asset folder as Embedded Resource.

4. Create a class for the component which wraps a WebView element based on the following pattern.

 
```csharp
namespace Zebble.Plugin
{
    using System;
    using System.Reflection;
    using System.Threading.Tasks;
    using Zebble;

    public partial class MyComponent : Canvas
    {
        WebView WebView;
        Assembly Assembly => GetType().GetAssembly();

        public override async Task OnInitializing()
        {
            await base.OnInitializing();
            WebView = new WebView(Assembly, "Zebble.Plugin").Size(100.Percent());
            await Add(WebView);
        }

        public override async Task OnPreRender()
        {
            await base.OnPreRender();
            WebView.Html = Assembly.ReadEmbeddedTextFile("Zebble.Plugin", "Asset/Index.html");
            // Of course you can customise the HTML code in C# code before rendering, for example to inject parameters into it.
        }
    }
}
```

You can add properties, methods, etc to define and build a state, parameters, ... in this C# class. This way anyone using the component will be able to interact with it as a simple C# based Zebble view and ignore the fact that it's implemented using the web technologies. Of course you will need to reflect such settings and configurations in the HTML code, or by using the WebView methods such as EvaluateJavascript(...).

#### Referencing assets

Since the Javascript, Image and Css files are embedded, when you reference them in the HTML file you should use the following syntax:

```xml
<html>
   <head>
      <script type="text/javascript" src="resource:SomeFolder/MyJavascript.js"></script>
      ....
      <link rel="stylesheet" href="resource:SomeFolder/Styles.css" />
   </head>
</html>
```

At runtime, the WebView component will recognise the special prefix of **"resource:"** and then load a resource with that name and merge it into the html file before rendering it.