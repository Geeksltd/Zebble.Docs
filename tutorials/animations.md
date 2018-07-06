[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-1.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-2.gif
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-3.gif
[4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-4.gif
[5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-5.gif
[6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/18-6.gif


### ANIMATIONS

In this lesson, you will learn:

- How to animate element properties such as position, size, rotation, opacity, etc.
- How to animate multiple properties at the same time.
- How to implement advanced timing using the standard .NET async programming features.
- How to configure advanced animation settings such as easing algorithm and factor.
- How to add entry animations declaratively in your markup file without C# code.

[Download this video directly](https://drive.google.com/file/d/0B3EED8dgociydERwUU0ySGI4MUU/view?usp=sharing)

[![INTRODUCTION TO ZEBBLE](https://github.com/Geeksltd/Zebble.Docs/blob/master/assets/tutorials/1.png?raw=true)](https://www.youtube.com/watch?v=Mtkv7w_Ktho)

-----------------------------------------------------------------------

#### Animation API

You can use the Animate() method of the View class to change any of its attributes as an animation.

#### Example 1 - Basic use:

The following code will animate the view to move to the right side by 100 pixels. The duration of the animation will be based on the static value of Animation.DefaultDuration which is 300ms.

```csharp
myView.Animate(x=> x.Margin(left: 100));
```
 
![1] 

#### Example 2 - Explicit duration:

The following example is the same as Example A, but it runs the animation in exactly 100ms.

```csharp
myView.Animate(100.Milliseconds() , x=> x.Margin(left: 100));
```

#### Example 3 - Multiple properties:

The following example will animate two properties, so you get a diagonal moving effect. 

```csharp
myView.Animate(100.Milliseconds() , x=> x.Margin(left: 100, top: 100));
```

You can animate the value of as many properties as you want. For example, the following will animate the view and fade it out at the same time.

```csharp
myView.Animate(100.Milliseconds() , x=> x.Margin(left: 100, top: 100).Opacity(0));
```

#### Example 4 - Advanced

You can create an Animation object to specify the full details of the animation and pass that to the Animate() method of a view. In fact, all the examples above are just shortcuts to the following:

```csharp
myView.Animate(new Animation
{
    Duration = TimeSpan.From....(...),
    Change = v => { /* Modify the view to its target state */ },
    Delay = TimeSpan.From....(...), // Optional
    Easing = AnimationEasing.[EaseIn | EaseInOut | EaseOut | Linear ]
});
```

One of the optional settings of animation is Easing. Easing is an Enum that determines the velocity of the changes during the course of animation. For example if it set to Linear, the speed of the transition will be fixed during the hole the animation. The default value is EaseOut which means the transition starts fast and then it slows down as the approach end of the animation.       

There is a box which is dyed blue:

```csharp
<Canvas Id="Box" Style="width:50; height:50px; background: blue" />" 
```

Now we want to animate it.

##### Sample 1:

```csharp
await Box.Animate(new Animation
{
Duration = 1.Seconds(),
Change = {} => Box.Rotation(90).Margin(left : 100)
)};
```

![2]

##### Sample 2:

```csharp
await Box.Animate(new Animation
{
Duration = 1.Seconds(),
Change = {} => Box.Rotation(90).Margin(left : 100)
Easing = AnimationEasing.Linear
)};
```

![3] 

##### Sample 3:


```csharp
await Box.Animate(new Animation
{
Duration = 1.Seconds(),
Change = {} => Box.Rotation(90).Margin(left : 100)
Easing = AnimationEasing.EaseInOut
)};
```
 
![4]


##### Sample 4:


```csharp
await Box.Animate(new Animation
{
Duration = 1.Seconds(),
Change = {} => Box.Rotation(90).Margin(left : 100)
Easing = AnimationEasing.EaseInOut
EasingFactor = EasingFactor.Quintic
)};
```

![5]

#### Advance Timing

Now we want to run multiple animations in parallel. For this, we use Task.WhenAll() function in C#.

video-to-gif output image

```xml
<Canvas Id="Box" Style="width:50; height:50px; background: blue" />"   
<TextView Id="Text" Text="Color:black" />
```

```csharp
await Task.WhenAll(
    Box.Animate(2.seconds(), x => x.Margin(left: 100)),
    Text.Animate(1.Seconds(), x=> x.TextColor(Color.Red))
    );
    
    // This line runs after 2 seconds
```


#### To wait, or not to wait?

The Animate() method returns a Task. You can await it if you want the rest of the calling code to run after the animation is completed. But often this is not the case, and you want to fire the animation to run whilst then doing other things. In that case, you should not await it.

#### Visual Studio Warning?

If you don't await the task Visual Studio might show you a warning. To get rid of it, you should do something with the Task that doesn't really do anything. For example, just call RunInParallel().

```csharp
myView.Animate(x=>...).RunInParallel();
```
 
#### AddWithAnimation

You can use View.AddWithAnimation() method instead of the Add() method to dynamically add objects on the screen.

##### Example:

We are setting the "z-animate-to" attribute to specify the final state of the object which is x=100 pixels and opacity is one for visible.

```xml
<Canvas Id="Box"
    Style="width:50; height:50px; background: blue; left:-50; opacity:0;"
    z-animate-to="X=100; Opacity=1;"
    z-animate-duration="1000" />
```

![6]

This is telling the rendering engine that my box is initially invisible and out side of screen, but as soon as the page is shown, then it will fly in.

- There is no C# code here and we achieved this with only setting the "z-animate-to" and "z-animate-duration" attributes.

We can implement this sample in C#:

```csharp
this.AddWithAnimation(new MyView(), initialState: v=>v.X = -v.ActualWidth, change: v => v.X = 0);
```
The above example, will slide the item into the screen from left side.