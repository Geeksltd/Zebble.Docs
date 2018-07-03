
### USING CUSTOM FONTS IN ZEBBLE

#### iOS:

1. Create a folder called Fonts in your iOS projects and add all fonts you need. You can only use **ttf** or **otf** files in iOS.

2. Add the following markup to your info.plist:

```xml
<key>UIAppFonts</key>
    <array>
        <string>Fonts/YOUR-FONT-NAME.ttf</string>
        <string>Fonts/YOUR-OTHER-FONT-NAME.ttf</string>
    </array>
```

3. Right click on your font and select the Properties. In properties of your fonts set these:

> Build action: Content <br>
Copy to output directory: Always copy or Copy if Newer

4. Use your custom font in Sass:

```css
TextInput, TextView { font-family: "Thonburi-Light"; }
```

You need to find the exact name of your font. If you are struggling to do so, paste this code at the end of your Initialize function of your AppDelegate and watch the Output window of Visual Studio for all available fonts in your device after doing all these steps:

```csharp
foreach(var font in UIKit.UIFont.FamilyNames)
            {
                foreach (var item in UIKit.UIFont.FontNamesForFamilyName(font))
                    Device.Log.Warning(item);
                Device.Log.Message("-----------");
            }
```

**`Important: Do not forget to remove this code once you found the font name.`**
 

#### Android: 

1. Add your font file to the Android Assets folder. You can only use ttf or otf files in Android.

2. Right click on your font and select the Properties. In properties of your fonts set these:

> Build action: AndroidAsset <br>
Copy to output directory: Always copy or Copy if Newer

3. Use your custom font in Sass:

```css
TextInput, TextView { font-family: "Thonburi-Light.ttf"; }
```

**`Important: Remember that you need to use the exact file name that you have in your Assets folder with the ttf or otf extension included.`**

 

#### UWP: 

1. Create a folder called Fonts in your Assets folder in the UWP project and paste your fonts in it. You can only use ttf or otf files in UWP.

2. Right click on your font and select the Properties. In properties of your fonts set these:

> Build action: Content <br>
Copy to output directory: Always copy or Copy if Newer

3. Use your custom font in Sass:

```css
TextInput, TextView { font-family: "Thonburi-Light.ttf"; }
```

**`Important: Remember that you need to use the exact file name that you have in your Assets/Fonts folder with the ttf or otf extension included.`**