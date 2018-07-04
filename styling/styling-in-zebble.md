[stylingwithzebble]: https://github.com/Geeksltd/Zebble.Docs/blob/master/assets/stylling/stylingwithzebble.png

### STYLING IN ZEBBLE

![stylingwithzebble]

Let us to see how the relationship between the CSS files and The Views work. Because unlike html where the CSS parsing and allocations happen by the browser engine, in Zebble we are dealing with native user interface objects and platform which obviously done under CSS. So it is trick that we are using here.

Inside the Zebble framework there is a class named **Stylesheet**. The View Class has two properties of that type. One of is **CSS** and one is **Style**. This means that you can effectively have two sets of style definitions for every View objects. The style settings will always override the ones in CSS setting 

Every **View** object has a property named **CssStyle** which is similar to HTML's class tag.

Zebble will look for all .CSS files in your App.UI folder to identify css settings.
It will then and then generate their **C# equivalent code** in **.zebble-generated-css.cs**.

**For example, the following CCSS code:**

```css
IconButton  #Icon {
    height: 20px;
    background-position: left;
    background-size: contain;
    margin-top: 5px;
    margin-left: 5px;
}
```

Will generate the following code:   

```csharp
[CssSelector("...MyFile.css", "IconButton #Icon")]
[CssBody("height: 20px; background-position: left; background-size: contain; margin-top: 5px; margin-left: 5px;")]
class IconButton_IconCssRule : CssRule
{
    // This method will determine whether the selector applies to a given view object.
    public override bool Matches(View view)
    {
        if (!(view.Id == "Icon")) return false;
        while (true)
        {
            if ((view = view.Parent) == null) return false;
            else if (view is IconButton) break;
        }
        return true;
    }

   // This method will actually apply the CSS body on the view object.
    public override void Apply(View view)
    {
        view.Height = 20;
        view.BackgroundImage.Alignment = Alignment.Left;
        view.BackgroundImage.Stretch = Stretch.Fit;
        view.Margin.Top = 5;
        view.Margin.Left = 5;
    }
}
```

Use the same best practices as you follow in web development. For example:

- Use CSS instead of hard-coding visual settings in the markup or C# code.
- Reuse styles as much as possible.
- Use semantic selectors, etc.
- You can mix and match classes and use all the usual powerful CSS features.