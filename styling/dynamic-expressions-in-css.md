
### DYNAMIC EXPRESSIONS IN CSS

You can use C# language in your CSS files, which is extremely powerful. But use this power responsibly and don't overdo it. To use C# expressions, you can use the CSS **calc("...code...")** function. Use the view keyword to gain access to the object you're styling.

**For example:**

```css
.my-class {
    height: 50px;
    margin-top: calc("view.Parent.ActualHeight - view.ActualHeigh / 2") ;
}
```

Will generate:   

```csharp
...
// This method will actually apply the CSS body on the view object.
 public override void Apply(View view)
 {
     view.Css.Height = 50;
     view.Css.Margin.Top = view.Parent.ActualHeight - view.ActualHeigh / 2;
 }
...
```

#### Dynamic Size & Position

You can also set Width, Height, X (Left) and Y (Top) in CSS as dynamic expressions. Normally such scenarios should be implemented using Binding [to other objects] in order to achieve responsive layouts. The following example shows how you can set the height of an object to always be 50px less than the height of the device and remain updated (e.g. if you rotate the device to swap width and height values).

```css
.my-class {
    height: calc("View.Root.Height, x => x - 50");
}
```

You have access to the full binding syntax. For example you can define a value to depend on multiple length objects. The following example ensures that the object's height is always the same as the device's height minus another object's height.

```css
.my-class {
    height: calc("View.Root.Height, SomeOtherView.Height, (x, y) => x - y");
}
```