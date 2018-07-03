
### NAV.FORWARD() VS NAV.GO()

To go from one page to another you can use either of the following methods:

```csharp
Nav.Forward<TargetPage>()
```
```csharp
Nav.Go<TargetPage>()
```

If you use Forward(), this enables the target page to then use Nav.Back() to come back to the current page. The way it works is that when you use Forward() then the current page will get added to the **navigation stack** (which is accessible using Nav.Stack). But when you use **Go()** then the stack gets **completely cleared** and so the target page will not be able to use Nav.Back().

**NOTE 1:**

The NavigationBar component is aware of the navigation stack. When there is anything in the stack, then instead of the burger menu icon it will add a "Back" button to the top left corner.

**NOTE 2:**

In **M#** when you have a navigate activity, by default it will generate Nav.Go<> instead of Nav.Forward<> which means you won't have the "Back" functionality on the destination page. To solve this in M# for your navigate activity, set **"Support going back"** to true.