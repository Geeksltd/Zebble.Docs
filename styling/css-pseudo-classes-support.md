
### CSS PSEUDO-CLASSES SUPPORT

Every view object in Zebble can define its current state using pseudo classes using the **":something"** added to the end of its normal selector.

**Example CSS:**

```css
.my-object { color: #000000; }
.my-object:active { color: #ff0000; }
```

The view code can turn itself into a  pseudo state by changing its **PseudoCssState** property.

**Example:**

```csharp
class SomeView : View
{
     ....
    OnSomethingChanged() 
    {
           this.SetPseudoCssState("active", someCondition);
    }
}
```

This is used by several built-in components. Also you can use this feature for your own custom elements.

#### Important Tip

When using pseudo-classes in Zebble it's important to explicitly provide a value for the default state. Unlike CSS behavior in Web, Zebble does not automatically undo the styles applied to an element's pseudo state. Instead, it will simply run all matching CSS rules on the element.

In the above example, our CSS code is effectively resetting the color of my-object to #000000 when it's no longer active.