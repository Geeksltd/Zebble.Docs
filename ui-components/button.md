[basicusage]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/BasicUsage.png "Zebble-Button"
[autosize0]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/AutoSize0.png "Zebble-Button"
[autosize]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/AutoSize.png "Zebble-Button"
[enableandignore]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/Enabled&Ignored.png "Zebble-Button"
[fontandcolor]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/Font&Color.png "Zebble-Button"
[fontandcolor1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/Font&Color1.png "Zebble-Button"
[boxshadow]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/BoxShadow.png "Zebble-Button"
[position]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/Position.png "Zebble-Button"
[texttransform]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/TextTransform.png "Zebble-Button"
[csssetting]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/CSSSetting.png "Zebble-Button"
[text]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/button/Text.png "Zebble-Button"


#### Button
Button inherits from TextView. It adds some default styling to make it look like a button.

##### Basic usage


<div style="float: left;width: 65%;text-align: left;">

```xml
<Button Id="MyButton" Text="Tap Me!" />
```
Or you can create it using C#:
```csharp
this.Add(new Button { Text="Tap Me!" });<!-- From a live URL -->
```

</div>
<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![basicusage]

</div>

<div style="clear: both;" />

<div style="float: left;width: 65%;text-align: left;">

##### AutoSize
```xml
<Button Id="MyButton" Text="Tap Me!"  AutoSizeWidth="false" Style.Border="1" />

<Button Id="MyButton" Text="Tap Me!"  AutoSizeWidth="true" Style.Border="1"/>
```

</div>
<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![autosize0]

![autosize]

</div>

<div style="clear: both;" />

##### Enabled & Ignored

Stylesheet has a boolean property named ***Ignored***, which is false by default. When set to true it works the same as **"display: none"** in HTML. It means that the element will not only be invisible, but also it **won't occupy space** on the screen.

View has a boolean property named ***Enabled***, which is true by default. When set to false the object will not respond to UI gesture events. But it will remain visible. Also, its PseudoCssState will be set to "disabled" which allows you to specify a visual style for it in CSS.


<div style="float: left;width: 65%;text-align: left;">

**MarkUp:**
```xml  
<Button Id="MyButton1"  Text="Button 1" />
    <Button Id="MyButton2"  Text="Button 2" Enabled="false" />
    <Button Id="MyButton3"  Text="Button 3" />
    <Button Id="MyButton4"  Text="Button 4" Ignored="true"/>
    <Button Id="MyButton5"  Text="Button 5" />
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;" >

![enableandignore]

</div>

<div style="clear: both;" />

##### PseudoCssState

PseudoCssState is a boolean value that if it will be set to "disabled", it allows you to specify a visual style for it in CSS.

##### Rotation

You can see some information about rotation in  Zebble here: http://zebble.net/docs/rotation-in-zebble

##### Margin & Padding

You can see some information about Margin & Padding in Zebble here: http://zebble.net/docs/margin-padding

##### Font and color

<div style="float: left;width: 65%;text-align: left;">

```xml
<Button Id="MyButton" Text="Tap Me!" Style.TextColor="#AA00BB" Style.Font.Name="Arial" Style.Font.Bold="true"/>
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;" >

![fontandcolor]

</div>

<div style="clear: both;" />

**Note:** It's strongly recommended avoiding using the Style directly unless you have to. Instead, you should use CSS to apply your styles.

<div style="float: left;width: 65%;text-align: left;" >

**MarkUp:**

```xml
<Button Text=" Button 1"  Style.BackgroundColor="green" />
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![fontandcolor1]

</div>

<div style="clear: both;" />

<div style="float: left;width: 65%;text-align: left;">

##### Box Shadow

```xml
<Button Text="Button 1" Style.BoxShadow.Color ="red" Style.BoxShadow.BlurRadius="15" Style.BoxShadow.XOffset="5" Style.BoxShadow.YOffset="5" Style.Border="1" />
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![boxshadow]

</div>

<div style="clear: both;" />

<div style="float: left;width: 65%;text-align: left;">

##### Text

```xml
<Button  Style.Height="30" Text=" Button 1" Style.Border ="1" TextAlignment="Right" Style.TextColor="gold"/>
<Button  Style.Height="30" Text=" Button 2" Style.Border ="1" TextAlignment="Middle"/>
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![Text]

</div>

<div style="clear: both;" />

<div style="float: left;width: 65%;text-align: left;">

##### Position

```xml
<Button Style.Height="30" Text=" Button 1" Style.Border ="1" Style.X="100" Style.Y="300"/> 
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![position]

</div>

<div style="clear: both;" />

##### TextTransform
You can set a text transform value to the style or css settings of a button. When you do so, the original Text value will hold the original casing, but when rendered on the platform, the transformation will be applied. It works just like html.

The supported values are

- None (same as the original text)
- Uppercase
- Lowercase
- Capitalize (first letter of each word will be upper case).

<div style="float: left;width: 65%;text-align: left;">

```xml
<Button Text="Hello World!" TextTransform="None"/>
<Button Text="Hello World!" TextTransform="Uppercase"/>
<Button Text="Hello World!" TextTransform="Lowercase"/>
<Button Text="hello world!" TextTransform="Capitalize"/>
```

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![texttransform]

</div>

<div style="clear: both;" />

##### Css settings

In addition to all common CSS settings such as border, padding, margin, etc, the following css settings are supported specifically for text view and its descendants such as Button:

<div style="float: left;width: 65%;text-align: left;">

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

</div>

<div style="float: right;width: 30%; text-align: right;margin: 10px;">

![csssetting]

</div>

<div style="clear: both;" />

You can set the Css of text view object by following below:

```xml
<TextView Id="MyText" Text="Hello World!" CssClass="MyTextClass"/>
```

##### Width

As a button inherits from TextView, it has the same functionality available for automatic sizing. For example:

```xml
<Button ... AutoSizeWidth="true"/>
```

##### Tapped Event

You can handle the tapevent by assigning the Tapped attribute in markup, or handling the **Tapped** event in code.

```xml
<Button Id="MyButton" Text="Tap Me" on-Tapped="@MyButtonTapped"/>
```

ViewModel:
```csharp
async Task MyButtonTapped()
{
      // Handle the event and take necessary actions here.
}
```
##### Navigation without event handler

If your button is meant to simply navigate to another page, instead of defining a tap event handler, you can use the pseudo attribute of `z-nav-forward` or `z-nav-go` to navigate to another page. 

```xml
<Button Id="MyButton" Text="Tap Me" z-nav-forward="Pages.SomeOtherPage"/>
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
