
### NAMING BEST PRACTICES

When defining views in your markup files, use the following rules:

#### Avoid setting Id unless you need it

Don't set Id unless you want to use it in code behind (or CSS). In the following example there is no benefit to setting the Id property and it's just adding noise to the code.

```xml
<TextView Text="Hello" Id="HelloTextView" />
```

Even when you want to use event handlers, still there is no need to set an ID. For example the following will be enough, and you don't need to set an ID for the button.

```xml
<Button Text="Go" on-Tapped="GoButtonTapped" />
```

#### Id naming

When you do need to set ID, use the shortest possible meaningful name, which is usually the same as the purpose or nature of that object.

For example:

```xml
<Stack Id="Actions">
     <Button Text="Edit" Id="Edit" />
</Stack>
```

There might be rare cases where there is a conflict. For example you may have different views with the same overall purpose such as the following example. In such cases, suffix the Id with the type of the view element.

```xml
<Stack Id="EditStack">
     <Button Id="EditButton" Text="Edit" />
     <Image Id="EditImage" Path="images/edit.png"
</Stack>
```

There may also be cases where the simple name would conflict with the property names of the base View class. For example imagine in a healthcare app you need the user to type in their height in a textbox. If you name the textbox as "Height" then it will conflict with the Height property of the base class. So in that case also you should use the type suffix. For example:

```xml
<TextInput Id="HeightTextInput" />
```

#### Event handler naming

To name your event handler methods, use the following patterm: {ViewName}{Event}

For example:

```csharp
async Task GoButtonTapped()
{
     ...
}

async Task ActionsStackPanning() => ...
```

#### Code behind -> Keep everything private

Any event handlers, fields, etc, that you define in your code behind will run in the same class that is generated for your mark-up. If you come from the ASP.NET WebForms background you might be used to making things protected or public to make them work. But it's unnecessary in Zebble. Simply drop the scope modifier (public, private, internal, protected) to reduce noise (everything will become private by default). 

#### Async method names

When the .NET asynchronous programming first came to be, there was a lot of traditional, non-async methods in APIs. The async methods started to get added one by one in libraries, and to distinguish between them it was recommended to suffix the async methods with the name "Async". For example:

```csharp
public void Something()
{
   ...
}

public Task SomethingAsync()
{
    ....
}
```

However, all Zebble projects are given birth in the modern day where async programming is the default, and the norm. For that reason pretty much all of your methods are probably going to be async and return a task, and you don't need to write a sync alternative of your methods.

**In this new world, the old recommendation to suffix all methods with "Async" is irrlevant and adds unnecessary noise**. So avoid it, and name your methods simply after what they do without adding the syffix of "Async".