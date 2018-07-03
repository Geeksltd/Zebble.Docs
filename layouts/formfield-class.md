[main]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/formfield-class/main.png "Zebble-Stack"
[sample1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/formfield-class/sample1.png "Zebble-Stack"
[sample2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/formfield-class/sample2.png "Zebble-Stack"

### FORMFIELD CLASS

`FormField<TControl>` is a convenient way to create a form element by encapsulating the following in :

- Label (or icon)
- Input control

All input controls can be a type of FormFild.

For example 

`FormField<TextInput>`, `FormField<DatePicker>`,
`FormField<TimePicker>`, `FormField<ItemPicker>`, `FormField<FilePicker>` and `FormField<Slider>`.


![main]
 

**Example**

![sample1]

```xml
<FormField z-of="TextInput" LabelText="First name:" Placeholder="..."   />
<FormField z-of="ItemPicker" LabelText="Type:"   />
<FormField z-of="Switch" LabelText="Select?"/>
```

You can of course create them in C#:

```csharp
var firstName = new FormField<TextInput> { LabelText="First name:", Placeholder="..." });
// ...
```

#### Icon (instead of label)

Instead of a label, you can use an icon. This is useful normally in combination with placeholder text. Although you also can provide both icon and label text.

```xml
<FormField z-of="TextInput" IconPath="Images/Icons/User.png" Placeholder="..."  />
```

#### Configuring the control

The **Control** property of a form field gives you access to the actual input control (Text input, item picker, etc) and you can then set its properties. For example:

```xml 
<FormField z-of="TextInput" ...  Control.TextMode="Password" />
```

#### Vertical arrangement

A vertical arrangement of the label and the control can be achieved by using the Direction property.


```xml
<FormField z-of="TextInput" ... Direction="Vertical"   />
```

![sample2]

**Note:** You can enable vertical allocation for the whole project using CSS. If that's your preference, as an exception, for CheckBox and Switch controls, it's usually more user-friendly to keep the control on the right-hand side.

```css
FormField { Direction: calc("RepeatDirection.Vertical"); }

FormField--Switch, FormField--CheckBox {
    Direction: calc("RepeatDirection.Horizontal");
    margin-top: 10px;
}  
```