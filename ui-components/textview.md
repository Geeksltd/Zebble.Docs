[basicusage]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/basicusage.png "Zebble-TextView"
[width]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/width.png "Zebble-TextView"
[width1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/width1.png "Zebble-TextView"
[enable&ignore]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/enable&ignore.png "Zebble-TextView"
[font&color]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/font&color.png "Zebble-TextView"
[boxshadow]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/boxshadow.png "Zebble-TextView"
[text1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/text.png "Zebble-TextView"
[text2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/text1.png "Zebble-TextView"
[position]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/position.png "Zebble-TextView"
[texttransform0]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/texttransform0.png "Zebble-TextView"
[texttransform1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/texttransform1.png "Zebble-TextView"
[texttransform2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/texttransform2.png "Zebble-TextView"
[texttransform3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/texttransform3.png "Zebble-TextView"
[csssetting]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/csssetting.png "Zebble-TextView"
[wrapping]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textview/wrrapping.png "Zebble-TextView"

#### TextView
TextView It's a simple class to show a piece of text. You can specify its font, size, bold, italic and color.

##### Basic usage

```xml
<TextView Id="MyText" Text="Hello World!" />
```

![basicusage]

Or you can create it using C#:

```csharp
this.Add(new TextView { Text="Hello world" });
```

##### Width

Like all other Zebble objects, the width of a TextView is determined by the general width rules, which means an even allocation of width among horizontal siblings. But if you want the TextView to take only the space needed by its actual text string and font, you can set AutoSizeWidth to **true**.

**MarkUp:**

```xml
<TextView Id="MyText" Text="Hello World!" AutoSizeWidth="true" Style.Border.Width="2" />
```
 
![width]

```xml
<TextView Id="MyText2" Text="Hello Galaxy!!" AutoSizeWidth="false" Style.Border.Width="2" />
```
 
![width1]

 
##### Enabled & Ignored

Stylesheet has a boolean property named ***Ignored***, which is false by default. When set to true it works the same as **"display: none"** in HTML. It means that the element will not only be invisible, but also it **won't occupy space** on the screen.

View has a boolean property named **Enabled**, which is true by default. When set to false the object will not respond to UI gesture events. But it will remain visible. Also, its PseudoCssState will be set to "disabled" which allows you to specify a visual style for it in CSS.

**MarkUp:**

```xml
<TextView Id="MyText" Style.Height="20" Text="TextView 1" />
<TextView Id="MyText" Style.Height="20" Text="TextView 2" Enabled="false" />
<TextView Id="MyText" Style.Height="20" Text="TextView 3" />
<TextView Id="MyText" Style.Height="20" Text="TextView 4" Ignored="true"/>
<TextView Id="MyText" Style.Height="20" Text="TextView 5" />
```

![enable&ignore]

##### PseudoCssState

PseudoCssState is a boolean value that if it will be set to "disabled", it allows you to specify a visual style for it in CSS.

##### Font and color

```xml
<TextView Id="MyText" Text="Hello World!" Style.TextColor="#AA00BB" Style.Font.Name="Arial" Style.Font.Bold="true"/>
```

![font&color]

##### Box Shadow

Zebble components have a special effect which is named BoxShadow. As you can see in next image, it has start X and Y position for effecting and the amount of radious.

```xml
<TextView Style.Height="40" Text=" TextView 1" Style.BoxShadow.Color ="red" Style.BoxShadow.BlurRadius="5" Style.BoxShadow.XOffset="5" Style.BoxShadow.YOffset="5" Style.Border="1"/>
```

![boxshadow]

##### Wrapping

TextView has a method named ShouldWrap() which determines whether the text should be wrapped. By default, it will return true when the text size is larger than 20 characters. But you can override it by setting the Wrap property manually.

```xml
<TextView ... Wrap="true"/>
```

![wrapping]
 
##### Text

```xml
<TextView Id="MyText2" Style.Height="30" Text=" TextView 2" Style.Border ="1" Style.TextColor="gold" />
```
 
![text1]

```xml
<TextView Id="MyText5" Style.Height="30" Text=" TextView 5" Style.Border ="1" TextAlignment="Middle" />
```

![text2]

##### Position
 
```xml
<TextView Id="MyText6" Style.Height="30" Text=" TextView 6" Style.Border ="1" Style.X="100" Style.Y="300"/>
```

![position]

##### TextTransform

You can set a text transform value to the style or css settings of a text view. When you do so, the original Text value will hold the original casing, but when rendered on the platform, the transformation will be applied. It works just like html.

The supported values are

- None (same as the original text)
- Uppercase
- Lowercase
- Capitalize (first letter of each word will be upper case).

```xml
<TextView Id="MyText1" Text="Hello World!" TextTransform="None"/>
```
![texttransform0]
```xml
<TextView Id="MyText2" Text="Hello World!" TextTransform="Uppercase"/>
```
![texttransform1]
```xml
<TextView Id="MyText3" Text="Hello World!" TextTransform="Lowercase"/>
```
![texttransform2]
```xml
<TextView Id="MyText4" Text="hello world!" TextTransform="Capitalize"/>
```
![texttransform3]

##### Css settings

In addition to all common CSS settings such as border, padding, margin, etc, the following css settings are supported specifically for text view and its descendants such as Button:

```css
.my-selector {
   color: #553300;
   text-transform: uppercase;
   font-family: 'Arial';
   font-weight: bold;
   text-align: center;
   vertical-align: top;
}
```

![csssetting]

You can set the Css of text view object by following below:

```xml
<TextView Id="MyText" Text="Hello World!" CssClass="MyTextClass"/>
```

### Events
| Event             | Type                                          | Android | iOS | Windows |
| :-----------      | :-----------                                  | :------ | :-- | :------ |
| on-Flashed            | AsyncEvent    | x       | x   | x       |
| on-Initializing            | AsyncEvent    | x       | x   | x       |
| on-LongPressed            | AsyncEvent    | x       | x   | x       |
| on-PanFinished            | AsyncEvent    | x       | x   | x       |
| on-Panning            | AsyncEvent   | x       | x   | x       |
| on-PreRendered            | AsyncEvent    | x       | x   | x       |
| on-Swiped            | AsyncEvent   | x       | x   | x       |
| on-Tapped            | AsyncEvent    | x       | x   | x       |
