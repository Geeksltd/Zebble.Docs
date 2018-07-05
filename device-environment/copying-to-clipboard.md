
### COPYING TO CLIPBOARD

The following code allows you to copy some text into clipboard:

```csharp
await Device.Sharing.SetClipboard("some text");
```

Android allows you to specify a label for the clipboard as well. If you want to use that feature then you can use the following overload:

```csharp
await Device.Sharing.SetClipboard("some text", "android specific label");
```

**Note:** the label will be ignored in iOS and Windows platforms.

 