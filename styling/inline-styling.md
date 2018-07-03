
### INLINE STYLING

Just like HTML, Zebble supports inline styling of elements. Again, the same as HTML, you should aim to use CSS whenever possible, and avoid inline styling as much as possible.

To achieve inline styling in your Markup you have two options:

#### Inline styling in Markup

**Option 1**

You can directly set the value of each style property in your markup. For example:

```xml
<TextView Style.TextColor="blue" Style.Font.Bold="true" Style.BackgroundImage.Path="Images/Something.png" />
```

**Option 2**

Alternatively you can set the combined value of Style, similar to HTML:

```xml
<TextView Style="color: blue; font-weight: bold; background: url(images/Something.png)" />
```

They both run with the same performance, and in fact, result in identical generated C# code in the .zebble-generated.cs file.

#### Inline styling in C#

**Option 1:**

You can set the values of If you need to specify the styles in C# then you have two options:You can 

```csharp
myView.Style.TextColor="blue";
myView.Style.Font.Bold=true;
myView.Style.BackgroundImage.Path="Images/Something.png";
```

**Option 2:**

Alternatively, you can use the fluent API, which allows you to use extension methods to set multiple styles in one line:

```csharp
myView.Font(bold: true, color: "blue").Background(path: "Images/Something.png");
```

#### Fluent API

Sometimes you need to set several properties of a view or a stylesheet in code behind. For example:

```csharp
myView.Style.Margin.Top = 20;
myView.Style.Margin.Bottom = 10;
myView.Style.Padding = 20;
myView.Style.Font.Size = 15;
myView.Style.Font.Bold = true;
```

**There is a better way**. Zebble provides fluent 'extention methods' to set all view and stylesheet properties. Each one will return the object back, so you can keep calling other methods on it. 

```csharp
myView.Style.Margin(top: 20, bottom: 10).Padding(20).Font(size: 15, bold: true);
```