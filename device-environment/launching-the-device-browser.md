
### LAUNCHING THE DEVICE BROWSER

Sometimes you want to open a URL inside the application (similar to Facebook) without opening a new app such as Safari. The browser should almost take the full size of the screen, except with a button to close it and go back to the app.

To do that, add a button with the following code:

```csharp
Device.OS.OpenBrowser(Url);
```