
### STANDARD ZEBBLE SETTINGS

#### Database settings

The following setting determines if the objects loaded from the local database should be cached in memory (for performance) or not:

```xml
<Database.Cache.Enabled value="true" />
```

The following settings determines the name of the SQLite database file used by the app.

```xml
<Database.File value="app.db3" />
```

#### Dev & Debugging

During development in a Windows (desktop) you can set Dev.Mode to true. It will allow you to "Ctrl + Click" on objects on the screen to launch the inspector. It will add additional run-time checks to help with problem diagnosis. 

```xml
<Dev.Mode value="true" />
```

#### Multi-threaded debugging

When you run into an exception it may not give you the full stack trace due to multi-threding issues ([learn more](https://github.com/Geeksltd/Zebble.Docs/blob/master/async-programming-multi-threading/debugging-the-stacktrace-problem.md)). If you set this flag to true then UIRuntime.StackTrace will give you the full picture.

```xml
<MultiThread.Debugging value="false" />
```

#### Performance profiling

If you want to profile your application for performance improvements it's important to remove any noise from background work. The reason is that such processes will impact the profilers' results, while they don't impact the real user's experience. One of the standard background processes in Zebble is Disposing the pages which are no longer reachable. That happens in the background, but it can massively impact your performance profiling data.

To isolate the performance data to only the page rendering and the standard flow, you can temporarily disable the background Disposing actions by setting the following config value to true. In addition you need to turn off the noise from the Zebble Inspector by setting DevMode to false..

```xml
<Profiling.Performance value="true" />
<Dev.Mode value="false" />
```

#### Disabling view caching

If you want to disable page caching you can add teh following setting which will result in all [CacheView] attributes being ignored. As a result when navigating to a page it will never be added to the navigation cache. So it will be recreated when you go there.

```xml
<Disable.View.Caching value="true" />
```

#### Styling & CSS

During development (Windows), you can uncomment the following line, in order to simulate another platform for use in the CSS engine for quicker testing.

```xml
<Dev.Css.Platform value="Android" />
```

The following determines whether the flash() method should be automatically invoked for Button and IconButton views before their tap event handler code is executed

```xml
<Button.Tap.AutoFlash value="true" />
```

#### Push notification

If you need the app to support receiving push notifications even when it's not running actively, then set the following to true:

```xml
<Push.Notification.Background.Enabled value="false" />
```

Also when you register your app with Google Play Services for Push Notifications, add the Sender ID. [Learn why](http://stackoverflow.com/questions/14044017/gcm-api-key-vs-sender-id).

```xml
<Push.Notification.Android.Sender.ID value="..." />
```

#### Shaking gesture

If you want your app to respond to the user shaking the phone, then you need to set the following:

```xml
<Device.System.DetectShaking value="true" />
```

#### Web API

To specify the base URL for your server application's Web Api used by the mobile app, use:

```xml
<Api.Base.Url value="https://123.123.123.123:7890" />
```

#### Application Rating

If you want to launch the App Store rating application directly from your app you should set the following:

```xml
<Application.Apple.ID  value="1166606853" />
<Application.Android.ID value="my.application" />
<Application.Windows.ID value="com.my-website.MyApplication" />
```

#### Android specific

When the user is looking at a page while there is no previous page in the navigation stack, if she then presses the back button nothing will happen. In that scenario, if you want the application to be minimised to show the Android home page, then you can achieve that behaviour by setting the following.

```xml
<Android.Hardware.Back.Can.Close value="true" />
```