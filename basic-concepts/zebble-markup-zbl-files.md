
### ZEBBLE MARKUP (.ZBL FILES)

Your UI pages and modules will be typically created as ZBL markup files which are XML files. The following shows a sample ZBL file.

```xml
<z-Component z-type="MyModule" z-base="Stack" z-namespace="UI.Modules"
    CssClass="my-module"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../../.zebble-schema.xml">

  <TextView Text="Hello World!"/>

</z-Component>
```

When the Zebble.EXE tool sees this ZBL file, it will generate the following class inside the .zebble-generated.cs file.

```csharp
namespace UI.Modules
{
    using System.Threading.Tasks;
    using Zebble;

    public class MyModule : Stack
    {
        public override async Task OnInitializing()
        {
            await base.OnInitializing();
            CssClass="my-module";
            Add(new TextView { Text = "Hello World!" });
        }
    }
}
```

#### z-Component

The root node of every .ZBL file is a z-Component element. Each z-Component element is converted into a C# class.

- The **class name** will come from the z-type attribute.
It **inherits** from a class specified in the z-base attribute. You can specify Zebble.View or any class inheriting from it.
- The **namespace** will come from the z-namespace attribute.
Any other attribute setting (e.g. CssClass) will be translated into a C# property setter.
In the markup file, inside the z-Component class, you can add the contents of your component such as Stacks, TextViews, Images, etc.

#### Nested z-Component

You can have z-Component nodes defined inside other z-Component nodes. When you do that, the generated C# class will be a nested class in the parent z-Component. This pattern is used for example for ListModules.

```xml
<z-Component z-type="MyModule" ...>
    ....
    <z-Component z-type="MyNestedClass" ...>
        ...
    </z-Component>
    ....
/z-Component>
```

#### `<z-Abc/>` vs `<Abc />` elements

When reading .ZBL markup files, you will notice that some elements start with "z-" while others don't:

- z-* elements are certain tags (or keywords) processed by the Zebble.EXE tool in a special way. They are not treated as content nodes.
Other elements are considered "content" nodes. They are converted, as they are defined, into the C# equivalent.
In the rest of this article, you will learn about some of the z-* keywords and what they mean.

#### Content elements and attributes.

Any element not starting with z-* is a content element.

- For each element, in the generated C# class, an object will be defined and added to its parent node in the initialization method.
- For each attribute, a property setter will be generated in C#.
- For example for the following markup:

```xml
<z-Component z-type="MyModule" ...>
     <A Id="a" Prop1="Val1">
          <B Id="b" />
     </A>
</z-Component>     
```

The initialization code will be generated as:

```csharp
public override async Task OnInitializing()
{   
       await base.OnInitializing();
       this.Add(a = new A { Id = "a", Prop1 = "Val1" });
       a.Add(b = new B { Id = "b" });
}
```

As you can see, because A is defined directly inside the z-Component node, it's added to "this", whereas B is added inside A. You can have a deep nesting of objects, and they will all follow this pattern.

z-Abc vs on-Abc vs Abc attributes
The z-* attributes have a special meaning and will not be translated into C# property setters.
The on-* attributes are treated as event subscribers (i.e. to attach an event handler to the Abc event)
Other attributes will be simply transferred into the C# code, as they are defined, as property setters.

```xml
<z-place inside="...">
```

Let's say you want to add a content element X inside another element named Y. If Y is defined in the same ZBL file, you can simply nest the <X/> declaration inside the <Y/> tag. But sometimes the parent element is not defined in the same ZBL file. You will have this scenario when the container (Y) is:

- Inherited from a base class of the z-Component. Or;
- Nested inside another element (e.g. your z-Component has <Z/> custom module which internally has a <Y/> inside it, and you want to inject your <X/> Inside the Y of Z.
- In such cases, you can specify the parent of an element by wrapping it inside a <z-place /> tag and specify the parent node as the value of "inside" attribute. For example:

```xml
<z-place inside="MyInheritedY">
     <X />
</z-place>
```

which will generate:

```csharp
...
MyInheritedY.Add(new X());
...
```

#### Embedding C# expressions

When setting an attribute value, you can use the @ character (just like Razor in ASP.NET MVC) you embed C# code in your markup file. For example: 

```xml
<TextView Text="@DateTime.Now.ToString()" />
```

#### `<z-loose>....</z-loose>`

In case you need to define an object in Markup, but you don't want to add it to any parent, you can nest it inside a <z-loose> element. This is useful if you want to dynamically add it to a parent in the C# code-behind file based on some runtime logic.


#### `<z-foreach var="..." in "...">`

z-foreach allows you to define a loop inside your markup, to repeat a particular markup fragment for every item in a data source. You should:

- Specify the loop variable using the **var** attribute.
- Specify the data source using the **in** attribute.

```xml
<z-Component z-type="MyModule" ...>
    <z-foreach var="item" in="new [] {1, 2, 3 ,4}">
         <TextView Text="@item.ToString()"/>
    </z-foreach>
</z-Component>
```

#### Id is optional, but...

When you add content elements, the Id attribute is optional.

- If you do specify an Id, it should be unique in the markup file.
When you specify Id for any element, then a public field will be generated in the C# class, allowing you to access that object from outside of that module as well.
- If an element has child elements (e.g. a Stack) and yet it has no Id, then Zebble.EXE will automatically name it UNNAMED_[TYPE] (e.g. UNNAMED_Stack) and make it private.

#### Intellisense
To provide intellisense during editing, ZBL files use an XML schema file named .zebble-schema.xml. This file is generated automatically by Zebble.EXE based on:

- Zebble object model
- Other ZBL modules and pages defined in your application.

**Important note:** The intellisense provided in the ZBL files is not perfect. It may list attributes that are not valid, and may not list attributes that would be valid. It's different from the C# intellisense which is pretty much always reliable.

- If you believe some code (e.g. attribute setter) is valid, yet it doesn't show up in the ZBL markup intellisense, write it anyway and compile. If the generated C# class accepts it, it's OK. If you get a compile error, then that's a bug you need to fix.
- If some attribute comes up in the intellisense, yet the generated C# class does not compile, it means that it's invalid in that context and you should remove it.