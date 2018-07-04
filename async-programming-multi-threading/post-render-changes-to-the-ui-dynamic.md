[problem]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/async-programming-multi-threading/problem.png

### POST-RENDER CHANGES TO THE UI (DYNAMIC)

In most cases you will define your UI modules using ZBL markup. But you can also create your UI using C#. In such cases you usually will use the OnInitializing event to create the UI, which occurs before the UI is actually rendered.

#### Changes at run-time (after rendering a page)

However there are cases when you need to modify or create parts of your UI dynamically after the page is rendered. For example you may need to set the "Ignored" property of some objects to true or false, in order to show or remove them from the screen. Such cases may lead to cascading changes on other UI elements. 

#### Example scenario

Imagine a vertical stack with 10 items. You dynamically then set the Ignored property of the 5th item to False when a button is clicked. At that moment the system will automatically rearrange the following items. Item 6 is shifted up to take the place of the 5th item which is now removed. Then item 7 needs to be moved up, ... to the end. Now the total height of the stack itself is also changed. And if the stack was itself hosted in another stack, then there is another cascading there, ....

This means that a lot of UI layout update work will start at the moment that you set Ignored = false on the 5th item. Now remember that all layout work in Zebble, including all user code runs on the background thread, including the cascading explained above.

#### The problem

![problem]

Normally the above scenario will work fine. However imagine that while the above code is running, you start another change which affects the layout as well. For example let's say the user clicks the button again, and now you want to toggle the Ignored attribute of that 5th item back to true.

In this case two concurrent threads of work start to change the layout, which can lead to inconsistent values and a messed up layout!

#### Zebble's limited defence

The above example won't actually happen with the same button, because Zebble by default will ignore subsequent user taps when the handler for the previous Tap is still running. But if you clicked another button which set that Ignored to true, then the above scenario can actually happen.

Also all other gesture events in Zebble will queue execution of your event handlers to minimise the chances of concurrent changes to the UI. But across difference UI controls, gesture events can run at the same time.

For example if you have two switch controls, both of which would trigger such a change, they can indeed run at the same time if the user toggles both of them quickly before the first one's action is completed.

#### The solution: Layout Synchronization

A built-in mechanism in Zebble allows you to implement dynamic changes in a safe way. First you need to determine the host view object that contains all the other objects involved in the layout change process. Often that is the module or page itself, where you're writing the code.

```csharp
async Task Button1Tapped()
{
      using (await DomLock.LockAsync())
      {
             // TODO: Apply the change that affects the layout
             // For example:    SomeObject.CssClass="abc";
      }
}

async Task Button2Tapped()
{
      using (await DomLock.LockAsync())
      {
             // TODO: Apply the change that affects the layout
             // For example:    SomeObject.CssClass="xyz";
      }
}
```

The DomLock object gives you a central point with which to synchronize layout changes across different event handlers.

#### When do you need it?

As a rule of thumb, you don't need to worry about this if your dynamic change is something quick and simple to process, such as changing the text of a label, modifying the background color of an object, setting the Visible or opacity, etc. 

But in other cases, or when your change involves a change to the layout, then to ensure parallel changes are not going to mess your layout, you need to correctly synchronise complex UI changes. For example changing Width, Height, Ignored, Margin, Padding or changing CssClass at runtime can lead to big changes.

#### Dynamic UI changes using UIWorkBatch

There are cases that you want to make UI changes at runtime, on the same already rendered page, for example as a result of a user tap event. If the change that you want to make is simple, such as changing the background color of an object, then simply setting the property will be fine. However, if your change involves cascading layout changes on other objects, the safe way to achieve that is via the following:

```csharp
await UIWorkBatch.Run(() => {
    // your change(s) go here
} );
```

Otherwise you can experience layout issues.

#### Under the hood

The fact that your code runs in the background thread rather than the UI thread is a great convinience. However, it can come at a cost. When at runt-time you change properties of a rendered view object, your changes are replicated on the native object automatically. In addition, your changes to one object may have a knock on effect on other views. For example if you change the height of an object in a vertical stack, the position of the items following that would need to be changed as well. If such changes lead to complex chains of cascading changes, there is a possibility that your native objects go out of sync, leading to rendering issues. To avoid this problem you should run such code in a single UIWorkBatch, which will suspend all native rendering until the full chain of cascading layout changes are done.