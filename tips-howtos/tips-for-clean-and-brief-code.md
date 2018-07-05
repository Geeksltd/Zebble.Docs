
### TIPS FOR CLEAN AND BRIEF CODE

The less noise in your code, the easier it is to read, understand and maintain. So you should try to remove any code that is unnecessary. It may not be always obvious what is unnecessary, but if you try to pay attention to this principle, you will be able to see more and more possibilities for cleaning up your code.

The following clean up options are highly recommended when developing Zebble apps:

#### Use GCop

Install the [GCop visual studio extension](https://marketplace.visualstudio.com/items?itemName=Paymon.GCop) and fix all errors and warnings it gives you. It has hundreds of useful code analysis rules.

#### Use "Clean up" from Geeks Productivity Tools

When you install [this Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=Paymon.GeeksProductivityTools) you can then right click on the Solution (or each project) in the Solution Explorer window named "Clean up". When you click on it, it will automatically do the following across your project:

- Organize and Remove unnecessary usings.
- Remove the "private" keyword where it's unnecessary.
- Remove duplicate blank lines from all C# files.
- ...

#### Remove unnecessary Ids

Don't set Id unless you want to use it in code behind (or CSS). In the following example there is no benefit to setting the Id property and it's just adding noise to the code.

```xml
<TextView Text="Hello" Id="HelloTextView" />
```

Even when you want to use event handlers, still there is no need to set an ID. For example the following will be enough, and you don't need to set an ID for the button.

```xml
<Button Text="Go" on-Tapped="GoButtonTapped" />
```

#### Use self closing tags

When an element in your ZBL markup has no children, use a self closing tag. For example:

```xml
<TextView Text="Hello" />
```

INSTEAD OF:

```xml
<TextView Text="Hello"></TextView>
```

#### Avoid event handler methods for simple navigation

If all a button needs to do is to navigate to another page, in the markup use the z-nav-.... tags and avoid creating an event handler method unnecessarily. [Read more](https://github.com/Geeksltd/Zebble.Docs/blob/master/navigation/navigation-without-event-handler.md).

#### Don't explicitly set default parameters to themselves

Many methods take optional parameters which have a default value. In those cases do not explicitly set the parameter value to the default one unnecesarily. For example:

```csharp
Nav.Forward<Pages.MyPage>(PageTransition.SlideForward);
// Remove "PageTransition.SlideForward" because that's the default transition anyway!
```

#### For APIs, use T[] array instead of `List<T>` or `IEnumerable<T>`

When your API methods return a list of objects, use an array type:

```csharp
return await Api.Get<Product[]>("api/v1/products...");
```

#### Use CSS instead of hardcoded styles 

Instead of hardcoding style related properties in C# or ZBL markup files, use CSS for anything possible.

#### Avoid complex C# code in Markup

Although you can write any C# expression in your ZBL markup files using the @ character, but you should avoid writing complex expressions. For example instead of:

```xml
<TextView Text="@Product.Count() + &quot; products&quot;" />
```

Define a property in your code-behind file and just call that in the markup:

```xml
<TextView Text="@ProductsCount" />
```
```csharp
string ProductsCount => Product.Count()  + " products";
```

#### Don't mess with the thread

Getting threading right in a mobile app is hard. But Zebble has gone a long way to simplify things for you. In Zebble apps, by default all app related code runs on the background thread and unless you aboslutely know what you're donig, you should conform to the following:

- Don't try to run anything directly on the UI thread. Forget about anything you may have learnt about dispatching work on the UI thread from other frameworks in the past. [Zebble is different](https://github.com/Geeksltd/Zebble.Docs/blob/master/async-programming-multi-threading/understanding-zebble-threading.md).
- Define every method in your app as async. Return a Task instead of void, or return Task<T> instead of just T. This will simplify things and you can  implement the [async all the way up](https://stackoverflow.com/questions/29808915/why-use-async-await-all-the-way-down) principle.
- Simply **await** the result of any async method call, and avoid things such as:
   - ... MyAsyncMethod().Wait();
   - ... MyAsyncMethod().Result;
   - ... MyAsyncMethod().GetAwaiter()...;
   - ... MyAsyncMethod().RunInParallel();    -----> Except for Animate() method
   - ...

#### Remove unnecessary Try/Catch blocks

Most APIs in Zebble already handle exceptions gracefully and show a user friendly alert to the user in case of any errors ([learn more](https://github.com/Geeksltd/Zebble.Docs/blob/master/debugging/exception-handling-in-zebble.md)). From Web Api client to Device hardware apis, this is supported by default.

So avoid wrapping such calls in your own try/catch block. In fact if you have a catch block which just shows an alert and return false, you probably don't need to use a try/catch at all. Make sure to learn how [Zebble handles exceptions](https://github.com/Geeksltd/Zebble.Docs/blob/master/debugging/exception-handling-in-zebble.md).

#### Remove unused files from App.UI\Resources

When creating a new project there are several sample files added to this folder. Also during the course of the project development you might add files which are no longer needed later on. Make sure to remove any files from there which are not used to reduce the size of your App Bundle when deploying to the App Stores, and also to eliminate confusion.

#### Keep code behind members private

When you define a field, method or property in a code-behind file of a .ZBL module, do not unnecessarily make it public or internal. This applies to your event handlers as well.