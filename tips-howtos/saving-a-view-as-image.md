
### SAVING A VIEW AS IMAGE

Sometimes you may need to create a screenshot image of a page, module, or any view that is rendered and is visible on the screen.

You can achieve that in Zebble using the following code:

```csharp
var imageFile = await Device.Screen.SaveAsImage(anyView);
```

In the above example, imageFile will be a FileInfo object referencing a PNG file stored under the device's local cache directory. You can do any kind of image processing, upload that via an API or do anything you want with this image.