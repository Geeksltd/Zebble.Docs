[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/navigation/showing-popup-pages/1.png

### SHOWING POPUP PAGES

To show a pop-up page you can use:

```csharp
// This will just create an instance of the specified target page type and then call the second overload (see below).

await Nav.ShowPopup<TargetPage>();
await Nav.ShowPopup(someView);
```

When you provide a view to be opened in a pop-up, Zebble will wrap your view in an instance of Popup class which is a page with some default style to make it look like a pop-up on top of an existing page.

**NOTE:** Many of the existing Zebble features such as Alert, ItemPicker, etc, internally use the Popup API.

![1] 

#### Sending parameters:

You can use an anonymous object to send parameters:

```csharp
wait Nav.ShowPopup<TargetPage>(new {Param1="...", Param2=...});
await Nav.ShowPopup(anyView, new {Param1="...", Param2=...});
```
 

#### Closing a pop-up

On the target pop-up page you will normally have a button to close the pop-up. That button should call the following to close itself:

```csharp
wait Nav.HidePopup();
```
 

#### Receiving a result back from the pop-up

There are cases where the parent host page needs to open a pop-up page, which in turn gets some input from the user, which should be then passed back to the host page. Zebble provides you with other overloads of the Nav pop-up methods to help you achieve that.

**Host page:**

```csharp
ar result = await Nav.ShowPopup<TargetPage, SomeType>();
// Now you can use "result".
```

**Pop-up page's close button:**

```csharp
..
await Nav.HidePopup(someResultValue);
```

**Notes:**

- SomeType can be a simple type such as boolean or string, or it can be a complex class.
- The type of the object returned by the pop-up must match the one expected by the host parent page.