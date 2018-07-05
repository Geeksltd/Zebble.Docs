
### ATTACHING CUSTOM DATA (TAG) TO OBJECTS

Sometimes you need to attach some custom data to your UI objects. For example in html you can use: <someTag **data-something**="some value" ... />. Also in Windows Forms and WPF you have the **Tag** «object» property which you can use as you like.

In Zebble each view has a property named Data which is a generic dictionary. You can use it to attach your custom data.

#### To set:

**In mark-up:**

```xml
<z-Component ....  data-MyKey="@MyValue"/>
```

**Note:** the data- prefix will be picked up by the Zebble build tool, and anything after that will be considered the Key. So the above code is equivalent to writing the following in code-behind.

**In code behind:**

```csharp
myView.Data["MyKey"] = myValue;

// Or alternatively:
myView.Data("MyKey", myValue);
```

#### To read:

```csharp
var value = (MyType)myView.Data["MyKey"];

// Or you can use this extension method  which does the casting internally:
var value = myView.Data<MyType>("MyKey");
```