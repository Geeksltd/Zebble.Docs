[tech&dev]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/introduction/what-is-zebble/teck&development.png "Zebble-Intro"

### WHAT IS ZEBBLE?

Zebble is a framework for developing natives for iOS, Android, and Windows from a **single source code** base.

It is a platform to develop cross-platform and multi-platform apps (Windows phone, Android and iOS). In Zebble platform, the code sharing concept is used. Zebble can be compared with the Xamarin Forms concept. But unlike Xamarin Forms, Zebble is for apps with custom UI designs and high-performance. Zebble is suitable for not only enterprise, but also consumer-facing apps.

#### Technology & Development

![tech&dev]

**C#:** Zebble apps are developed using Xamarin, C# and .NET framework. You can use the native or third party Xamarin components and almost all of your existing C# libraries as long as they are compatible with Xamarin.
 
**CSS and Markup:** Thanks to the Zebble build utility (zebble.exe,) your application UI code will be written mostly in Markup and CSS, with a very declarative syntax, just like web apps. Your code is then converted into C# for execution and debugging.
 
**100% Native:** Zebble provides you with many abstract UI elements, which are mapped to the native controls on each platform at runtime. Your app UI code is essentially written using this abstract UI language without worrying about the native implementations. Zebble apps are not hybrid. They execute with top performance.

#### Development Experience

**Development Speed:** In addition to the native mobile platforms, Zebble also has a special Windows rendering engine which you use primarily during development. It allows you to compile and run the app instantly upon every change and get immediate feedback for faster development. Unlike Xamarin Forms or other technologies you don't have to wait for 1-2 minutes for the simulator or device compilation and warm-up to run and test every change in your code.
 
**Less code:** The framework's concepts and fluent API allow you to write the same app with less code, compared to Xamarin Forms.
 
**Faster to run:** Zebble's engine is very efficient and the apps feel faster than Xamarin Forms.
 
**Extensibility:** Zebble UI system has a small core, i.e. view objects that actually mapped to native controls. All other components are just composed of other Zebble views. To create new custom controls, you also just put Zebble view objects together and don't have to deal with the platform specific rendering.
 
**Managing Resources:** In Xamarin Forms, the app resources are duplicated in each platform-specific wrapper project, making it harder to manage them. Zebble gives you a central location to store files, and manages all the bundling, etc automatically.

#### Visual Design

**Design-led:** Xamarin Forms renders the app differently on each platform to mimic the default application style and colors, which makes it inherently hard to achieve a customized visual design.  Zebble instead is design-led. Your app can therefore look the same on all platforms without seeming odd. It encourages you to create a custom visual design for your app - just like how you do with websites. So your app can look unique and pro, and ready for consumer facing.
 
**Powerful Styling using CSS:** Zebble's styling system allows you to centrally define the styles using CSS which is dramatically more powerful and efficient than the Xamarin Forms way. The CSS code in Zebble is automatically converted to the equivalent C# code to be executable in a native world.
 
**Unified styling:** Native platforms typically provide very different mechanisms to style different things that makes learning and code sharing difficult. Zebble introduces generalized visual attributes such as background (color or image), borders, paddings, rounded corners, etc. You can set these on any View object, just like HTML. So you get more fine-grained control and flexibility than Xamarin Forms.
