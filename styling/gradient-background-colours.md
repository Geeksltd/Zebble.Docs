
### GRADIENT BACKGROUND COLOURS

You can the background color of any view to a GradientColor instead of a plain Color.

The GradientColor class inherits from Color, but allows you to specify the gradient direction (default is Top-Down) as well as individual colour components.

For each colour component you can specify the colour and its percentage of the total view to cover, before swiching to the next colour. If you don't specify the percentage it will use 35% as default.

**Simple examples:**

```csharp
myView.BackgroundColor = new GradientColor(Colors.Grey, Colors.Black); // Change from 35%

myView.BackgroundColor = new GradientColor(Colors.Grey, Colors.Black, changeatPercentage: 50);
```

**Advanced example:**

```csharp
myView.BackgroundColor = new GradientColor(Direction.Right)
.Add(Colors.Black, 20)
.Add(Colors.Orange, 30)
.EndWith(Colors.White);
```

The above example will create a left-to-right gradient which starts with plain black for the first 20% of the total width of the object, then fades to orange from 20% point to another 30% (reaching the 50% of the object to this point), then fades to white in the remaining 50% of the object's width.