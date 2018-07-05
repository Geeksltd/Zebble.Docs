
### PROMPT FOR RATING THE APP

You should first add the following keys to config.xml file.

Replace the values with those of your own app.

```xml
<Application.Apple.ID>1166606853</Application.Apple.ID>
<Application.Android.ID>my.application</Application.Android.ID>
<Application.Windows.ID>com.my-website.MyApplication</Application.Windows.ID>
```

Then in the app UI code, the button used to launch the app rating external application on the mobile OS should call the following:

```csharp
Device.OS.OpenBrowser(Device.OS.GetAppRatingUrl());
```