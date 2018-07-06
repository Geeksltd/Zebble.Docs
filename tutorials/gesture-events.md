[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/7-1.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/7-2.png
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-1.png
[4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-2.png
[5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-3.gif
[6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-4.png
[7]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-5.gif
[8]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-6.png
[9]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-7.png
[10]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-8.gif
[11]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-9.png
[12]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-10.gif
[13]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/22-11.png

### GESTURE EVENTS

#### How to use an event in Zebble

We want to create a simple sample that has a TextView and a SearchInput components. When the user types a string and selects Search button, the string is shown in TextView automatically.

First of all, we create a page named **Page-5** with this Markup code:

**Page-5.zbl**:

```xml
<?xml version="1.0"?>
<z-Component z-type="Page5" z-base="Templates.Default" z-namespace="UI.Pages"
    z-partial="true" Title="About us" data-TopMenu="MainMenu" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
  <z-place inside="Body">
<TextView Id="txt1" ></TextView>
  <SearchInput Id="MySearchInput" on-Searched="ApplySearch" />
  </z-place>
</z-Component>
```

As you can see, we determine that when the **on-Searched** event is raised, the **ApplySearch** method is executed.

![1]

For implementing the **ApplySearch** method, you should go to **Page-5.cs** file:

```csharp
partial class Page5
{
    public override async Task OnInitializing()
    {
        await base.OnInitializing();
        await InitializeComponents();
    }
    async Task ApplySearch()
    {
        txt1.Text = MySearchInput.Text;
        // In this example I want to pass the keywords to an API to implement the search logic on the server.       
    }
}
```

The result page is same this image:

![2]
 

**Note:**

Previously events like Tapped and LongPressed optionally provided an event argument of type Point. 

Now all gesture events provide a single XXXEventArgs argument which will wrap the other parameters in them.

**Following, the gesture events of Zebble have been described:**

#### 1- Tapped

The tapped event is fired when the user tapps a view. 

![3] 

#### Samples:

in this sample, the user tapped on the TextView. After that, the alert with "Hello you!" is shown on the screen:

##### Sample 1:

```xml
<TextView Id="Something" Text="Tap me!" on-Tapped="SomethingTapped" />
```
```csharp
Task SomethingTapped() => Alert.Show("Hello you!");
```

![4] 

##### Sample 2:

```xml
<TextView Id="Something" Style.Height="50" Style.Width="50" Style.BackgroundColor="brown"  on-Tapped="SomethingTapped" />
```
```csharp
Task SomethingTapped()
{
if (Something.Width==50) Something.Width=100;
else
Something.Width=50;
return Task.CompletedTask;
}
```

![5]

#### 2- LongPressed

Every view has a long press event. When you hold an element with your finger for a full second it will be fired.

**Note:** In Windows desktop (during development), you fire that event by **right clicking** the object instead of holding the mouse key down.

![6]

##### Sample 1 :

```xml
<TextView Id="Something" Text="Tap me!"  on-LongPressed="SomethingTapped" />   
```

##### Sample 2:

This sample demonstrates using the LongPressed to implement dragging an image.

In this sample, we have an image in MarkUp:

```xml
<ImageView Id="MyImage" Path="Images/Something.png" on-LongPressed="CallDrag"/>
```

We use the argument which pass to the CallDrag for moving the image object:

```csharp
Task CallDrag(LongPressedEventArgs args)
{
      MyImage.Style.X= args.X;
      MyImage.Style.Y= args.Y;
      return Task.CompletedTask;
}
```

![7]
 
##### Sample 3:

In This sample, we demonstrate how using the LongPressed to implement dragging an image to the Remove box for simulating deleting an image. When users want to remove an image, they should select it and press for a long time for raising LongPressed events. After that, they drag it on a image which we called it Remove box.

In this sample, we have an image in MarkUp:

```xml
<ImageView Id="MyImage" Path="Images/Something.png"  on-LongPressed="CallDrag"/>
<ImageView Id="RemoveImage" Path="Images/remove.png" />
```
We use the argument which pass to the CallDrag for moving the image object:

```csharp
Task CallDrag(LongPressedEventArgs args)
{
    MyImage.Style.X= args.X;
    MyImage.Style.Y= args.Y;
    if args.X >= RemoveImage.X && args.Y >= RemoveImage.Y
    {
       // Do something for removing
    }
    
    return Task.CompletedTask;
}
```

#### 3- Panning & PanFinished

Every view in Zebble supports the following gesture events:

![8]

**Panning:** Happens when the user is touching the view and moving the finger (or mouse).

This is raised many times, for every tiny movement (one pixel or more).
Your event handler can take the starting and ending point.
 
```xml
<TextView Id="Something" Text="Tap me!"  on-Pannig="SomethingTapped" />  
````
  

**PanFinished:** Happens at the end of a panning batch when the finger or mouse button is release
<TextView Id="Something" Text="Tap me!"  on-PanFinished="SomethingTapped" />  

You can use these events to create custom user interactions and advanced scenarios.

**Example:**

Try the following example, which makes a draggable object that you can freely move around with a tiny bit of code!

```xml
<Canvas Id="Board" on-Panning="BoardPanning">
     <Canvas Id="Bullet" />
</Canvas>
```

**Note:**

Previously events like Tapped and LongPressed optionally provided an event argument of type Point. 

Now all gesture events provide a single **XXXEventArgs** argument which will wrap the other parameters in them.

```csharp
Task BoardPanning(PannedEventArgs args)
{
      Bullet.X(args.To.X).Y(args.To.Y);
      return Task.CompletedTask;
}
```

```css
#Board { height: 400px;}
#Bullet { background: blue; height: 40px; width:40px; border-radius: 20px; position:absolute }
```

#### 4- Swiped

It's fired when the user pans towards left or right for at least 20 pixels.

![9]

**Sample**

```xml
<TextView Id="Something" Style.Height="50" Style.Width="150" Style.BackgroundColor="brown"  on-Swiped="SomethingTapped" />  
```
```csharp
Task SomethingTapped()
{
    switch (Something.BackgroundColor.Tostring())
    {
      case "brown": 
        Something.BackgroundColor = "black"; 
        break; 
      case "black":
        Something.BackgroundColor = "green";
        break;
    }
    
    return Task.CompletedTask;
}
```
 
![10]

##### 5- Pinching
 

This event is fired when the user uses two fingers that go towards or away from each other.

The primary use case for this is to implement a custom zoom-in or zoom-out behaviour.

**Note:** In **Windows** desktop (during development) you should hold the **Ctrl** key and turn the mouse wheel up or down to invoke this event.

![11]
 
**Example**

```xml
<TextView Id="Something" Style.Height="50" Style.Width="50" Style.BackgroundColor="brown"  on-Tapped="SomethingTapped" />
```
```csharp
Task SomethingTapped()
{
    MyImage.Height= args.X;
    MyImage.Width= args.Y;
    return Task.CompletedTask;
}
```
 
![12]

#### 6. UserRotating

You can handle the UserRotating event to handle the gesture when the user is using two fingers in the motion demonstrated here.

The main use case for this gesture is to rotate your view on the Z index and it's common in Map applications.

**Note:** In **Windows** desktop (during development) you should hold the **Shift** key and turn the mouse wheel up or down to invoke this event.

 ![13]

#### Exceptions

Most of any application's code runs when the user provides an input, often in the form of a gesture. In other words often everything starts from an event handler such as tapping of a button.

Of course any code may have bugs including your event handler, and everything else that is invoked in a chain from there. If there is an unhandled exception the default behaviour of iOS, Android and Windows is to crash the app and close it immediately. That's not helpful for debugging, or for user experience.

To solve this problem event handlers in Zebble always catch any unhandled exception and display an error pop-up to the user, unless you're running the app with a Debugger attached, in which case the error will be thrown, allowing you go about your debugging the normal way.
