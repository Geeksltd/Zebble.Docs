
### NAVIGATION WITHOUT EVENT HANDLER

If a view such as your button is meant to simply navigate to another page, instead of defining a tap event handler, you can use the pseudo attribute of **z-nav-forward** or **z-nav-go** to navigate to another page.  This saves you from having to define an event handler.

```xml
<Button Text="Tap Me" z-nav-forward="Pages.SomeOtherPage"/>
```

#### Specifying transition

You can specify the transition effect if you don't want the default one to be used (which is usually SildeForward).

```xml
<Button Text="Tap Me" z-nav-forward="Pages.SomeOtherPage" z-nav-transition="SlideUp"/>
```

#### Sending parameters

If your target page acceps one or more parameters, you can also send parameters to the target page declaratively using the following format:

```xml
<Button Text="Tap Me" z-nav-forward="Pages.SomeOtherPage" z-nav-params="Param1=123, Param2=SomeObject, Param3=SomeMethod()"/>
```

Whatever you write here will be wrapped in a `new { ... }` block to create an anonymous object. Therefore, :

- If you have multiple parameters, use comma to separate them.
- The key of each parameter should be a valid C# identifier, ideally as PascalCase.
- The value can be any valid C# expression.
- The total value of z-nav-params should of course be a valid XML attribute value. This means that if you want to use double quotes to send string parameter values, you should XML encode them:

```xml
<Button ... z-nav-params="Param1=&quot;Some text&quot;"/>
```

- Alternatively if you find the &quot; too ugly, you can call a method or property which returns the string value.

#### Performance boost

When you use this approach for navigation, it not only is cleaner and quicker to implement, but also helps with Zebble optimization as well. When you use this format Zebble can know about the target pages to which you can go from the current view, and can therefore prepare such pages if needed, to improve the overall user experience and app responsiveness.