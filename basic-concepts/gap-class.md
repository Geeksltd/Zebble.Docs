
### GAP CLASS (FOR PADDING AND MARGIN)

Margin and Padding are two examples of the Gap class.

It allows you to set a fixed value for each side of an object: Top, Left, Bottom, Right.

**1. Uniform padding:**

```xml
<TextView Id="MyText" Text="Hello world" Style.Padding="4" />
```

**2. Side-specific paddings:**

```xml
<TextView Id="MyText" Text="Hello world" Style.Padding.Left="4" />
```

**3. Multiple side-specific paddings**

```xml
<TextView Id="MyText" Text="Hello world" Style.Padding.Left="4" Style.Padding.Bottom="2" />
```

#### Settings via CSS

The same settings can be applied using CSS, which is cleaner and must be your default choice.

**Markup:**

```xml
<TextView Text="Hello world" CssClass="my-text" />
```

**Css:**

```css
.my-text { padding: 4px;  padding-top:10px; margin: 10px 5px; }
```

#### Expressions and % based

You can also set the value of padding and margin based on percentage or a dynamic expression. For example:

```css
.my-text { padding: 4%;  padding-top: calc("View.Root.Height, view.Height, (r,h) => r - h / 2"); }
```