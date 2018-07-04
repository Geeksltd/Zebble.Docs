
### ZEBBLE CSS: UNDER THE HOOD

#### Special transformations

Some CSS settings are understood and transformed in a special way (hard-coded in the Zebble generator tool).

For example, if in your CSS file you use:

```css
.something { position: absolute; text-transform: uppercase; }
```

It will generate the following.

```csharp
public override void Apply(View view)
{
    view.Css.Absolute = true;           
    view.Css.TextTransform = TextTransform.Uppercase;
}
```

Other examples include "background-image", color settings, padding, and margins, etc.

#### General transformations
For anything other than the above, it will just transfer your CSS code to the generated C#. It doesn't even care if it's a valid code or not. For example:

```css
.my-class { font-size: 14px; Whatever=5px; }
```

then it will generate:

```csharp
...
view.Whatever = 5;
...
```

This gives you the ability to set custom component properties of any type in your CSS, which can be powerful.

#### Important note: type-specific properties

When you use CSS to set properties that are specific to certain types as opposed to all views (e.g. Direction of a Stack) then you must include the element type. It can of course also have class or ID selectors too, but the type part is mandatory.

**Example:**

```css
/* WRONG: */
#MyStackId { Direction = calc("RepeatDirection.Horizontal"); }

/* CORRECT: */
Stack#MyStackId { ... }
```