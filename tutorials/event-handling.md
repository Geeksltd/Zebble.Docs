[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/7-1.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/7-2.png

### EVENT HANDLING

In this lesson, you will learn how to handle events in Zebble, from user gestures to input controls and system wide events.

It will explain the problem with the traditional event model of C# in the modern world of asynchronous programming, and how Zebble's innovative approach will address them.

[Download this video directly](https://drive.google.com/file/d/0B3EED8dgociyZm1BTkRnVXFaMFk/view?usp=sharing)

[![EVENT HANDLING](https://github.com/Geeksltd/Zebble.Docs/blob/master/assets/tutorials/1.png?raw=true)](https://youtu.be/vZsGDBNKliA)

---------------------------------------------------------------

#### .NET Events: Problem Background

The standard event definition API in C# has been designed before the age of Task Parallel Library. Pretty much all .NET event handlers return a void as opposed to a Task. This means that it's not possible to await the code that subscribers register for an event.

#### Zebble's solution

The good news is that as Zebble has been designed in 2016, all of its events support asynchronous programming. You might notice that the Zebble events are members of type AsyncEvent as opposed to the traditional EventHandler type. The AsyncEvent type provides the pipework for defining, subscribing to and raising events.

Zebble UI events such as Tabbed, Swiped, etc, are in one of the following types:

- AsyncEvent
- AsyncEvent<TArg>
- AsyncEvent<TArg1, TArg2>

#### Subscribing to (i.e. handling) an event

To add event handlers you can use any of the following methods. Suppose you have a View object named **MyView** and you want to handle its **LongPressed** event. You have 2 options to attach an event handler. You can either use the Handle() method on the event object, or use the On method on the view.

```csharp
// Option 1
MyView.LongPressed.Handle(HandlerMethodName);

// Option 2 (recommended):
MyView.On(x => x.LongPressed, HandlerMethodName);
The benefit of the second option is that it returns the MyView object, so you can use it as a fluent API.
```

#### Task or void?

Your event handler can be a **task** or **void**. Or you can use a lambda expression. If your event handler is a VOID instead of TASK returning method, then you must explicitly cast it to Action as for some reason the C# compiler is not smart enough to infer the right overload.

```csharp
{
     ...
     MyView
         .On(x => x.LongPressed, MyTaskHandler)
         .On(x => x.LongPressed, (Action) MyVoidHandler)
         .On(x => x.LongPressed, () => ...(logic)...);
}
```
```csharp
Task MyTaskHandler()
{
    // handling code here...
}
```
```csharp
void MyVoidHandler()
{
    // handling code here...
}
```

#### Parameters are optional

Some events provide arguments. For example, the **Tapped** event provides a **point** object to tell you exactly where on the object the user tapped. However, in many scenarios, you may not care about that. In Zebble, your event handlers don't have to accept arguments if they don't need it.

```csharp
MyView.On(x => x.Tapped, MyFirstHandler);
MyView.On(x => x.Tapped, MySecondHandler);
// I don't need the parameter.
Task MyFirstHandler()
{
     // ...
}

// I do need the parameter.
Task MySecondHandler(Point point)
{
     //....
}
```

#### Unsubscribing event handlers

You can use the RemoveHandler() method on an event object if you want to unsubscribe.

```csharp
MyView.LongPressed.RemoveHandler(HandlerMethodName);
```

Though, when a view object is disposed, it will automatically unregister its event handlers. So you don't have to worry about keeping cyclic references between objects which could traditionally cause garbage collection issues.

#### Handling thread

By default, the event handlers will run on the same thread that raises the event. However, if you specifically need your handler to run on the UI thread you can use the **HandleOn()** method instead. This is only needed in very rare cases that you want to manipulate the native components directly, e.g. in platform-specific code.

```csharp
MyView.LongPressed.HandleOn(Device.UIThead, HandlerMethodName);
```

#### Creating your own events

If you want to create your own events, also you can use this model. The following shows the code pattern to implement it correctly.

```csharp
class MyCustomView : View
{
   ....
   // Simply define an instance of AsyncEvent to declare one.
   public readonly AsyncEvent SpecialEvent = new AsyncEvent();

   ....
   async Task SomewhereScenario()
   {
        ....
        // The following will invoke all the registered subscribers sequentially in the order they were subscribed.
        await SpecialEvent.Raise();

       // Alternatively, you can raise them in parallel
       await SpecialEvent.Raise(inParallel: true);
   }

   ....

   // Make sure to dispose it
   public override Dispose()
   {
        base.Dispose();
        SpecialEvent?.Dispose();
   }
}
```

#### Example Project

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