[main]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/sizing-and-positioning/main.png "Zebble-Size"
[def]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/sizing-and-positioning/defvalues.png "Zebble-Size"

### SIZING AND POSITIONING

Zebble has a modern and highly flexible layout engine which is extremely powerful. This is how it works.

Every view object has certain layout related properties such as Width, Height, X, Y, Padding.Left, Padding.Right, .... These properties are not simple numeric types, but rather of a smart type named Length which is explained below. 

![main]

#### Length <-> Responsive Design

Responsive Design is an approach to UI development that makes use of flexible layouts. The goal of responsive design is to build pages that detect the visitor's screen size and orientation and change the layout accordingly. Mobile devices have a very diverse range of sizes. So when designing your app's UI, for things like width, size, location, etc, you should think in terms of RULES rather than FIXED SIZES, to enable your UI to automatically adjust to the target device's screen.

The Length class in Zebble is an abstraction of, well, the length of things such as width or height of objects. It represents a logical size concept and can be set based on any of the following:

- **Exact value** based on *logical pixels*: For example 20px.
- **Percentage**: For example 20% (meaning 20% of container's size)
- **Automatic by Content**: For example for a TextView you may want the width to be based on the actual text and font.
- **Automatic by Container**: For example an object's width to fills its parent's available space (considering other siblings).
- **An expression**: Any C# expression.
- **Bound to another length**: For example my width to be the same as the vertical sibling above me, what ever that may be.
- **Bound to a function of another length**: For example my width should be the same as the vertical sibling above me minus 50px.
- **Bound to a function of other lengths**: For example my width should be always the max of two other object's widths, what ever they may be.

In all the scenarios above, except the first one, the actual value of a length object will depend on some other views, which themselves could depend on other views, etc. When you set up the value rule correctly using any of the above options, the Length object will update itself to always be the correct value at each point in time which means you don't have to worry about events, and triggers, and keeping things in sync.

Length has a property named CurrentValue (float) which represents its current logical pixel value at each moment in time. For example to query the exact width of a view object, you can use:

```csharp
return myView.Width.CurrentValue;
```

CurrentValue is read only and its value can, and often will, change throughout a rendering cycle. So you should generally avoid using it directly to adjust the size of something else, you are probably making a mistake, and should use the binding expressions instead.

#### Exact value
To set an exact value for a length object you can use any of the following methods:

**In markup**:

```xml
<SomeView Style.Width="150" .../>
```

**In Css**:

```css
.some-selector {
   width: 150px; /* px and pt will be interpreted the same */
   left: 20px; /* for setting X use the CSS standard attribute of left. Actually you can set X too, and it works, but Visual studio will show a warning :(*/
   top: 50px; /* same as above for Y */
}
```

**In code behind**:

```csharp
myView.Width.Set(150);
myView.Width.Set(SomeMethodThatReturnsFloat());
...
```

Please note that a fixed value in Zebble is a logical point and not a physical device screen pixel. For example for the width of an iPhone 4, you have 320 logical pixels, but 640 physical pixels. Every physical screen has a screen density which represents how many logical pixels there are for each logical one. For example an ultra high HD new smartphone may have pixel density of 4, meaning you have 4 hardware pixels per logical pixel.

To give you a bit of a background, in the past, before the invention of ultra high resolution screens, when you said "20 pixels" it usually meant around one centimetre. That's why people got used to the idea of using "pixels" to talk about sizes. Obviously today it's a different story and every display technology has a completely different physical density. The standard term of "point" was introduced in the Web CSS world to combat this, but people still confuse the two together and use the terms interchangeably.

In your UI thinking, you should only care about the logical pixels. For that reason Zebble treats both **px** and **pt** in your CSS code the same and assume you mean logical pixels. It will automatically handle the screen density for you in the render engine. 

#### Percentage value

To set an object's size based on its parent you can use the percentage option. When you do this, the size of the object will be bound to the size of the parent and if that changes, the child's will change automatically too.

**In markup**:

```xml
<SomeView Style.Width="30%" .../>
```

**In Css**:

```css
.some-selector {
   width: 30%; 
}
```

**In code behind**:

```csharp
myView.Width.Set(30.Percent());

// Or:
myView.Width.SetPercent(30);
...
```

**Note: Padding & Margin**

All objects are considered as "border-box" meaning that padding is contained within the width, not added to it. When you have % based width and height, the percentage will be applied to the parent's size minus its padding. For example

> Child's actual size = Percentage * (ParentSize - Parent Padding)


The same applies to X and Y accordingly. For example you can set an object's X to be 20%, which means its X position will be set to 20% of its parent's width minus its horizontal padding.

#### Automatic sizing

Another approach for setting a value for Width, Height is to specify an automatic sizing which is any option of the ***AutoStartegy*** enum:

**Content:** The view's width or height should be calculated as the sum of its children. <br>
**Container:** The view's width or height should be a proportional amount of the available space in its parent. If it's inside a parent of type stack, then the result will depend on its siblings within that stack.


#### Default values:

![def]

The following values are set as default, which will apply unless your CSS files or custom settings override them.

- Height -> AutoStrategy.Content
- Width -> AutoStrategy.Container
  - Except for ImageView which is -> Content

In other words by default Zebble assumes that the height of an object is meant to grow based on its children. But its width is mean to be limited to its parent. **Why?** The reason for that is that in terms of mobile UX best practices, horizontal scrolling is generally not ok (except for carousel, etc) while vertical scrolling is natural and expected.

#### Auto Width by Container

In practice most objects' width will be set based on **AutoStrategy.Container** as this is the default value. In that case the actual value will be based on the following rules:

- If it's not hosted inside a horizontal stack parent, then it will fill the parent's width minus the parent's horizontal padding and its own horizontal margin:
       ***Effective width => Parent.Width - Parent.HorizontalPadding - Own.HorizontalMargin***
- If it's in a horizontal stack then its width will be automatically set based on the parent's width as well as its other children:
   - **AvailableSpace** = Parent.Width - Parent.HorizontalPadding - Sum[Own and Siblings' Horizontal Margin])
   - **UnclaimedSpace** = AvailableSpace - Sum of Width of siblings with specific width (px, %, or AutoStrategy.Content)
   - **MyShare** = UnclaimedSpace / (1 + Count of siblings with AutoStrategy.Container)

In other words, the available space will be equally divided between all stack children of this type (i.e. no specific width value demand).

#### Auto Width by Content

When an object's width is set as **AutoStrategy.Content** it will be based on the following rules:

- For an ImageView the width will be determined by the actual image dimensions. It finds the aspect ratio of the image and calculate the width based on the Height of the ImageView. If Height is also set to be based on AutoStrategy.Content then the exact width of the source image will be used.
- For a TextView (and its subclasses such as Button) it will be calculated based on the font, padding and actual text. Note: with AutoSizeWidth set to True, can determine
- For a horizontal stack, it will be the sum of its children's width, horizontal margins and the stack's own horizontal padding.
- For all other views, it will be based on its widest child view (width + margin) plus its own horizontal padding. 

#### Automatic Height (Container or Content)

Calculation of the automatic height follows similar rules as that of Width (see above). Just replace width with height and that you can figure it out. 

#### Effective X (left)

When an object is inside a horizontal stack, then its effective X will be calculated from its left margin and its position in the stack (considering previous siblings' total width).
Otherwise, if an object has a value for X explicitly set, that will be returned with similar rules as Width (px, %, auto).
Otherwise, (when it's not absolute positioned) its effective X will be the same as its Left Margin plus its parent's left padding.

#### Effective Y (top)

When an object is inside a vertical stack, then its effective Y will be calculated from its top margin and its position in the stack (considering previous siblings' total height).
Otherwise, if an object has a value for Y explicitly set, that will be returned with similar rules as Height (px, % or auto).
Otherwise, (when it's not absolute positioned) its effective Y will be the same as its top margin plus its parent's top padding.

#### Expressions & binding

Sometimes you need an object's size or position to be calculated based on other objects. In such cases logically you'll have an expression, or function that determines you intended value. For example let's say you have objects A and B on top of each other and you always want B's width to match that of A. If you just set B's width to the CURRENT value of A's width, if then A's width is changed in the future (by CSS, code, device rotation, etc) then they will go out of sync.

To solve this problem, the Zebble layout system introduces an incredibly powerful mechanism whereby you will define your width values as time-less expressions (or functions) of other values. Zebble will then take care of calculations, cascading and keepings things up to date automatically. 

The following example will bind the Width of B to be always the same as A:

```csharp
B.Width.BindTo(A.Width);
```

The next example will bind the width of B to be always half that of A. In this example the variable "a" referes to the actual width of A which can change in the future, and yet B will remain in sync with it.

```csharp
B.Width.BindTo(A.Width, a => a / 2);
```

The next example will bind the width of B to be always the same as the Width of A minus the width of another object named C. In the code below, variables "a" and "c" will refer to the always-current values of "A.Width" and "C.Width". The order in which the parameters are defined determines the meaning of the variables in the lambda expression.

```csharp
B.Width.BindTo(A.Width, C.Width, (a, c) => a - c);
```

This can go on and you can add ass many parameters this way as you want. For example:

```csharp
B.Width.BindTo(A.Width, A.Height, B.X, C.Width, (aw, ah, bx, cw) =>(aw - ah) + bx * 2 - cw);
```

#### UpdateOn() 

When using expressions, sometimes you may want to use variables in your expression which are not necessarily of type Length. For example let's say you have a TextInput named "ti" and you want its Width to match its text size. You can write the following:

```csharp
ti.Width.BindTo(() => ti.Font.GetTextWidth(ti.Text));
```

In the above example, we have no dependency on another Length object and so no parameter is provided to our expression. However, the expression does depend on two elements which can change, i.e. Text and Font of the TextInput control. To ensure that our expression will get reevaluated in the future upon changes in Font or Text, we need to introduce a dependency to those right after defining the binding. So the correct code would be the following:

```csharp
ti.Width.BindTo(() => ti.Font.GetTextWidth(ti.Text)).UpdateOn(ti.FontChanged, ti.UserTextChanged);
```

The UpdateOn() method can take any number of AsyncEvent objects.

#### MinLimit & MaxLimit

You can add special constraints about the minimum or maximum acceptable value for a length. If you specify this then that rule will override the actual value defined by the other methods.

```csharp
myView.Width.Set(100);
// Now the current value is 100.

myView.Width.MaxLimit = 50;
// Now the current value will be 50

myView.Width.Set(20);
// Now the current value will be 20

myView.Width.MinLimit = 30;
// Now the current value will be 30;
```