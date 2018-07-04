[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/debugging/2.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/debugging/3.png

### DEBUGGING LAYOUT AND STYLES

![1]

Every view object has style related properties such as X, Y, Width, Height, Margin, TextColor, .... The effective value for each item is determined by either the direct Style setting of that object, or the most specific CSS rule which defines a value for that setting.

When the effective value for any style property comes from CSS (instead of inline Style) then you can easily see the situation to understand which CSS rules are being picked up and applied to your view and in what order.

#### Direct styles

But there are cases when you need to set certain properties via Style property directly. For example:

```csharp
myView.Background(color: Colors.Blue);
// Which is the same as:
myView.Style.BackgroundColor = Colors.Blue;
```

In these cases when you look at the object's properties in the inspector you can see the value (blue, in the example above) but you can't see exactly where and when this is being set. So if the value is incorrect, you might not immediately be able to see when this is being set.

In particular, consider scenarios when a complex mesh of event handlers is leading to a style property being set which you can't figure out how or even know where to start looking.

#### Solution: Layout Tracker

Zebble comes with a creative solution for this problem. This is how it works:

![2]

Using the inspector you identify the style property (width, height, etc) which has the wrong value.
There is a magnifying glass icon next to it which means **"set up a tracker"**
In this moment, the Zebble engine will register a tracker for that element and the page will refresh.
Open the Output window in Visual studio while the app is running.
You will notice that it's now reporting every time that style property is set, along with the stack trace, allowing you to see exactly what's going on.