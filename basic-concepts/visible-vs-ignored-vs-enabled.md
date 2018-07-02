
### VISIBLE VS IGNORED VS ENABLED

#### Visible Property

Stylesheet has a boolean property named Visible, which is true by default. When set to false it works the same as **"visibility: hidden"** in HTML. It means that the element will still **occupy space** on the screen, and it will just not be visible.

**Setting it in CSS:**

```css
.my-selector { visibility: hidden ; }
```

**Setting in code:**

```csharp
myView.Style.Visible = false;
```

**Setting in Markup:**

```xml
<SomeView Id="myView" ...  Style.Visible="false" />
```

#### Ignored Property

Stylesheet has a boolean property named Ignored, which is false by default. When set to true it works the same as **"display: none"** in HTML. It means that the element will not only be invisible, but also it **won't occupy space** on the screen.

**Setting it in CSS:**

```css
.my-selector { display: none; }
```

**Setting in code:**

```csharp
myView.Style.Ignored = true;
```

**Setting in Markup:**

```xml
<SomeView Id="myView" ...  Style.Ignored="true" />
```

It's important to understand this especially in relation to relative sizing.

For example in a horizontal stack, the child components take their width as an equal share between all siblings. When one sibling is not Visible, it still occupies the space. So if you want the other siblings to take its space, then you should set **Ignored=true** instead.

 
#### Enabled Property

View has a boolean property named Enabled, which is true by default. When set to false the object will not respond to UI gesture events. But it will remain visible. Also, its PseudoCssState will be set to "disabled" which allows you to specify a visual style for it in CSS.

```css
Button:disabled { opacity: 0.5; }
```
```csharp
MyButton.Enabled = false;
```
```xml
<Button ...  Enabled="false" />
```