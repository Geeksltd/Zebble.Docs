
### SETTINGS FILE: CONFIG.XML

In the App.UI project there is a file named **Config.xml** (under Resources folder).

This file contains all application config data. In a way it's **similar** to **web.config** in web applications.

However, this file is a flat list of key values in the format of:

```xml
<my.key>VALUE</my.key>
// OR:
<my.key value="VALUE />
```

To retreive the values in the application at runtime you can use the following code:
 
```csharp
Config.Get<TValueType>("my.key")
```