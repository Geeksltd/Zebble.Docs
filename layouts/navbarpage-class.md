[main]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/navbarpage-class/buttons.png "Zebble-Stack"

### NAVBARPAGE CLASS

This a sub class of the Page class which provided added functionality for a **Navigation Bar** (at the top)

#### Benefits

- The nav bar gets a fixed position at the top and isn't affected by scrolling.
- The contents of this page, added to the **Body** stack, will be scrolled below the nav bar.
- When navigating to another page using **slide forward** and **slide back** effects, the nav bar will not move. Instead, its content will fade to change.

#### NavBar buttons

![main]

In the inheriting pages and their modules, you can place buttons inside the navigation bar such as the one in this example. The button can be added to the right or left side of the navigation bar. You can achieve this using either of the following methods.

**ZML markup**

```xml
<Button Text="Something..." CssClass="navbar-button" ... z-navBar="right" />
```

**Programatically in C# code:**

```csharp
 await Page.GetNavBar().AddButton(ButtonLocation.Right,
      new Button { Text = "Something...", CssClass = "navbar-button" }.On(x => x.Tapped, SomethingTapped));
```