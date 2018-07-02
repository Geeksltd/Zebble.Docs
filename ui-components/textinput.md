[basicusage]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/basicusage.png "Zebble-TextInput"
[font&color1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/font&color1.png "Zebble-TextInput"
[font&color2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/font&color2.png "Zebble-TextInput"
[enable&ignore]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/enabled&ignored.png "Zebble-TextInput"
[placeholder]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/placeholder.png "Zebble-TextInput"
[keyboardactiontype]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/keyboardactiontype.png "Zebble-TextInput"
[lines]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/lines.png "Zebble-TextInput"
[boxshadow]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/boxshadow.png "Zebble-TextInput"
[position]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/position.png "Zebble-TextInput"
[textaligndesc]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textaligndesc.png "Zebble-TextInput"
[textalign]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign.png "Zebble-TextInput"
[textalign1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign1.png "Zebble-TextInput"
[textalign2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign2.png "Zebble-TextInput"
[textalign3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign3.png "Zebble-TextInput"
[textalign4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign4.png "Zebble-TextInput"
[textalign5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign5.png "Zebble-TextInput"
[textalign6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign6.png "Zebble-TextInput"
[textalign7]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign7.png "Zebble-TextInput"
[textalign8]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textalign8.png "Zebble-TextInput"
[textcolor]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textcolor.png "Zebble-TextInput"
[texttransform]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/texttransform.png "Zebble-TextInput"
[texttransform1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/texttransform1.png "Zebble-TextInput"
[texttransform2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/texttransform2.png "Zebble-TextInput"
[texttransform3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/texttransform3.png "Zebble-TextInput"
[textmodedesc]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textmodedesc.png "Zebble-TextInput"
[textmode]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textmode.png "Zebble-TextInput"
[textmode1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textmode1.png "Zebble-TextInput"
[textmode2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textmode2.png "Zebble-TextInput"
[textmode3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/textinput/textmode3.png "Zebble-TextInput"

#### TextInput
It allows the user to enter a text. It's similar to the Textbox control in the web world.
You can specify the line numbers, TextAlignment, Placeholder, Text Mode and Text Color.

##### Basic usage:

```xml
<TextInput Id="MyTextInput" Placeholder="Text here" TextMode="GeneralText"  TextAlignment="Justify"></TextInput>
```

```csharp
new TextInput { Id = "MyTextInput", TextMode = TextMode.GeneralText, 
TextAlignment = Alignment.Justify, Placeholder = "Text here"};
```

![basicusage]

 
##### PseudoCssState

PseudoCssState is a boolean value that if it will be set to "disabled", it allows you to specify a visual style for it in CSS.

##### Font and color

```xml
<TextInput Text="TextInput 1" Style.Border="3" Style.Border.Color="red" Style.BackgroundColor="gold"/>
```
 
![font&color1]

 ```xml
<TextInput Text="TextInput 2" Style.Border="3" Style.Border.Color="red" Style.BackgroundColor="brown"/>
```
 
![font&color2]

##### Enabled & Ignored

Stylesheet has a boolean property named ***Ignored***, which is false by default. When set to true it works the same as **"display: none"** in HTML. It means that the element will not only be invisible, but also it **won't occupy space** on the screen.

View has a boolean property named **Enabled**, which is true by default. When set to false the object will not respond to UI gesture events. But it will remain visible. Also, its PseudoCssState will be set to "disabled" which allows you to specify a visual style for it in CSS.


**MarkUp:**

```xml
<TextInput  Style.Height="20" Text="SearchInput 1" />
<TextInput  Style.Height="20" Text="SearchInput 2" Enabled="false" />
<TextInput  Style.Height="20" Text="SearchInput 3" />
<TextInput  Style.Height="20" Text="SearchInput 4" Ignored="true"/>
<TextInput  Style.Height="20" Text="SearchInput 5" />
```
 
![enable&ignore]


##### PlaceHolder:
 
The placeholder text shown when Text is null or empty. The default value is null.

```xml
<TextInput Id="MyTextInput"  Placeholder="Please Enter something here...!"/>
```

![placeholder]


##### KeyboardActionType:

If instead of "Go" you want the submit button to have a different text or icon, you can set the **KeyboardActionType** property to any of the following values:

- Go
- Continue
- Done
- Join
- Next
- Search
- Send

![keyboardactiontype]

##### Lines:

The Lines proeprty determines how many lines does InputText component have.

```xml
<TextInput Lines="5" Style.Border="1" Style.Border.Color="red"/>
```

![lines]


##### Box Shadow

Zebble components have a special effect which is named BoxShadow. As you can see in next image, it has start X and Y position for effecting and the amount of radious.

**MarkUp:**

```xml
<TextInput Style.Height="40" Text=" SearchInput 1" Style.BoxShadow.Color ="red" Style.BoxShadow.BlurRadius="5" Style.BoxShadow.XOffset="5" Style.BoxShadow.YOffset="5" Style.Border="1"/>
```

![boxshadow]

##### Margin & Padding

You can see some information about Margin & Padding in Zebble here: http://zebble.net/docs/margin-padding

##### Position

The location of an object can be determined by **Style.X** and **Style.Y**.

**MarkUp:**

```xml
<TextInput Id="MyTextInput" Style.Height="30" Text=" InputBox 1" Style.Border ="1" Style.X="100" Style.Y="300"/>
```

![position]


##### TextAlign:

Gets or sets the horizontal alignment of the text displayed in the object.


![textaligndesc]


**MarkUp:**

Sample 1:

```xml
<TextInput Id="MyTextInput" TextAlignment="Right" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.Right;
```
 
![textalign]

Sample 2:

```xml
<TextInput Id="MyTextInput" TextAlignment="TopLeft" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.TopLeft;
```

![textalign1]

Sample 3:

```xml
<TextInput Id="MyTextInput" TextAlignment="TopRight" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.TopRight;
```
 
![textalign2]

Sample 4:

```xml
<TextInput Id="MyTextInput" TextAlignment="TopMiddle" Text="My Text" Style.Border.Color="green">
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.TopMiddle;
```

![textalign3]
 
Sample 5:

```xml
<TextInput Id="MyTextInput" TextAlignment="Left" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.Left;
```
 
![textalign4]

Sample 6:

```xml
<TextInput Id="MyTextInput" TextAlignment="Middle" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.Middle;
```

![textalign5]

Sample 7:

```xml
<TextInput Id="MyTextInput" TextAlignment="BottomLeft" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.BottomLeft;
```

![textalign6]

Sample 8:

```xml
<TextInput Id="MyTextInput" TextAlignment="BottomRight" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.BottomRight;
```
 
![textalign7]

Sample 9:

```xml
<TextInput Id="MyTextInput" TextAlignment="BottomMiddle" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextAlignment = Alignment.BottomMiddle;
```
 
![textalign8]


##### TextColor

TextColor sets the color of the Text whick shown in the object.

**MarkUp:**

```xml
<TextInput Id="MyTextInput" Style.TextColor="white" Style.BackgroundColor="black" Text="My Text" Style.Border.Color="green"/>
```

C#:

```csharp
MyTextInput.TextColor = Zebble.Color.Parse("#A2B044");
```

![textcolor]


##### TextTransform

This property determine the output format of text:

- None: The output is same to the text.
- Uppercase: The all character of output is uppercase.
- Lowercase: The all character of output is lowercase.
- Capitalize: Only the first character of each work is uppercase.
 

**MarkUp:**

Sample 1:

```xml
<TextInput  Style.Border.Color="green" Lines="3" Text="ZEBBLE framework" TextTransform="None"/>
```

![texttransform]
 
Sample 2:

```xml
<TextInput  Style.Border.Color="green" Lines="3" Text="ZEBBLE framework" TextTransform="Uppercase"/>
``` 

![texttransform1]

Sample 3:

```xml
<TextInput  Style.Border.Color="green" Lines="3" Text="ZEBBLE framework" TextTransform="Lowercase"/>
```
 
![texttransform2]

Sample 4:

```xml
<TextInput  Style.Border.Color="green" Lines="3" Text="ZEBBLE framework" TextTransform="Capitalize"/>
```

![texttransform3]
 
##### TextMode

You can set the output format of text. By default, text mode is **Auto**, which allows Zebble to guess the correct TextMode depending on the Id of the control.


![textmodedesc]

sample 1:

```xml
<TextInput  Style.Border.Color="green"  Text="ZEBBLE framework" TextMode="GeneralText"/>
```

C#:

```csharp
MyTextInput.TextMode = TextMode.GeneralText; // This affects the keyboard.
```
 
![textmode]

Sample 2:

```xml
<TextInput  Style.Border.Color="green"  Text="Farhad.abaei@gmail.com" TextMode="Email"/>
```

C#:

```csharp
MyTextInput.TextMode = TextMode.Email; // This affects the keyboard.
```

![textmode1]
 
Sample 3:

```xml
<TextInput  Style.Border.Color="green"  Text="0123456" TextMode="Password"/>
```

C#:

```csharp
MyTextInput.TextMode = TextMode.Password; // This affects the keyboard.
```
 
![textmode2]

Sample 4:

```xml
<TextInput  Style.Border.Color="green"  Text="343434343434" TextMode="Decimal"/>
```

C#:

```csharp
MyTextInput.TextMode = TextMode.Decimal; // This affects the keyboard.
```

![textmode3]
 
##### Actions:

This control also has various event handling methods including: FocusChanged, TextCompleted, Clear, TextChanged, FontChanged etc. Any event handler usage is similar to each other, you just have to specify the method you want to handle events in it. For example:

```csharp
MyTextInput.TextChanged = TextChanged;
private void TextChanged() { /* Do something here*/ }
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
| on-UserFocusChanged            | AsyncEvent   | x       | x   | x       |
| on-UserTextChanged            | AsyncEvent   | x       | x   | x       |
| on-UserTextChangeSubmitted            | AsyncEvent   | x       | x   | x       |
| on-Tapped            | AsyncEvent    | x       | x   | x       |
