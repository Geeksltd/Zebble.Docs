
### DATA BINDING AND MVVM

Data bindings allow properties of two objects to be linked so that a change in one causes a change in the other. This is a very valuable tool, and while data bindings can be defined entirely in code, Zebble markup provides shortcuts and convenience.

Bindings are used most often to connect the visuals of an app with an underlying data model, usually in a realization of the MVVM (Model-View-ViewModel) application architecture. When using Zebble, you can use the MVVM pattern thanks to its support for Data Binding, but you don't have to. (If you're not familiar with MVVM, there are plenty of resources on the web to get you started).

#### Bindable `<TValue>`

Data bindings connect properties of two objects, called the source and the target. The first step is to define a **source** property in your code-behind class to which your view properties will be bound.

```csharp
readonly Bindable<string> MyProperty = new Bindable<string>("initial value");
```

*Bindable<TValue>* is a special type in Zebble which provides the functionality to broadcast changes to one or more subscribers.

To set a value for this property you can either use the Set() method or the Value property. For example:

```csharp
// .... To change the value anywhere in your code you can use:
MyProperty.Set("New value");
// Or:
MyProperty.Value = "New value";
```

As soon as a new value is set, all target objects which are bound to this will have their specified property updated as explained below.

#### Binding a visual property (markup)

As you may remember in Zebble markup you can use the @... value prefix syntax to specify a dynamic C# expression as opposed to a literal value.

```xml
<TextView Id="MyTextView" Text="@some c# expression..." />
```

If instead of just @ you use the **@{...}** syntax then Zebble code generator will understand thta it's a binding scenario and generate the appropriate code  to realise the binding. For example:

```xml
<TextView Id="MyTextView" Text="@{MyProperty}" />
```

You can see that in the .zebble-generated.cs file Zebble will generate the following C# equivalent line, which is what you can also write manually in case you want to create a binding in code-behind instead of markup:

```csharp
MyTextView.Bind("Text", MyProperty);
```

Alternatively you can use the AddBinding() method of the Bindable object to achieve the same result. This is particularly helpful if you want to create a binding to a non-View object of any type:

```csharp
MyProperty.AddBinding(MyTextView, "Text");

// Or to benefit from intellisense and compile time checking:
MyProperty.AddBinding(MyTextView, nameof(MyTextView.Text));
```

#### Expression-based binding

There are times when you may want to bind the target property to a function of a bindable property (source) as opposed to its direct value.  In those cases you can specify an optional lambda expression to provide the conversion logic.

**Example 1:**

Let's say you have a Bindable<int> property whose value may change at runtime.

```csharp
readonly Bindable<int> MyProperty = new Bindable<int>();
```

And you need to display it on the UI but only if it's not Zero. You can achieve that using the following: 

```xml
<TextView ... Text="@{MyProperty}" Visible="@{MyProperty, x=> x != 0 }" />
```

In the above example, the visible property (which is boolean) is being data-bound to a function of the bindable value which is defined as a lambda expression "x => x != 0" and is seperted by a comma from the name of the bindable property "MyProperty".

**Example 2:**

Let's say you have a DateTime property:

```csharp
readonly Bindable<DateTime> MyProperty = new Bindable<DateTime>();
```

And you want to display only the Time part on the UI:

```xml
<TextView ... Text="@{MyProperty, x=> x.ToShortTimeString()}" />
```

#### Tip: Background of data binding syntax in .NET
If you have any experience with MVVM implementations such as WPF, Xamarin Forms or UWP, you may know that to define a bindable property in such frameworks you have to write a lot more code, compared to Zebble. In those frameworks to just create a bindable property you have to do all of the following:

Your class should implement the INotifyPropertyChanged interface.
You should define an event object to broadcast the changes.
You should define a property that will invoke the event explicitly. For example

```csharp
class MyViewModel : INotifyPropertyChanged
{
     DateTime myProperty;
     public event PropertyChangedEventHandler PropertyChanged;

     public DateTime MyProperty
     {
           get => myProperty;
           set
           {
                 if (myProperty == value) return;
                 myProperty = value;
                 PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(nameof(MyProperty)));
           }
      }
}
```

None of this is required in Zebble as the Bindable<TValue> class will take care of everything. All you need to do is to define a readonly instance of Bindable<...> in your class. This means that in Zebble it's much quicker, cleaner and easier to implement data binding, or a full MVVM architecture.