[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/ui-with-c/1.png "Zebble-UI"
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/ui-with-c/2.png "Zebble-UI"
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/ui-with-c/3.png "Zebble-UI"

### INTRODUCTION TO UI WITH C#

One of the feature of Zebble framework is that everything you can create with MARKUP you can create with C# too.

![1]

As you can see in App.UI in your Solution Explorer, each MarkUp Page in Zebble is implemented in C# Class with the same name.

![2] 

In the C# code, there is a method named **InitializeComponents()** that has all C# UI codes that create your project.

After going to definition of **InitializeComponents** method, you can see the equivalent C# code of MarkUp. When you change the MarkUp file (*.zbl) and compile the project, the framework creates the equivalent C# codes in zebble-generated.cs file. 

![3] 

#### Sample

**MarkUp Exmple:**

```xml
<Grid Id="MyGrid" Direction="Vertical" Columns="2" Style.Height="90"  >
    <TextView Text="Row 1, left cell" Style.TextColor="red"/>
    <TextView Text="Row 1, right cell" />
    <TextView Text="Row 2, left cell" />
    <TextView Text="Row 2, right cell" />
    <TextView Text="Row 3, left cell" />
    <TextView Text="Row 3, right cell" />
</Grid>
```

**Equivalent C# Code:**

```csharp
await MyGrid.Add(new TextView { Text = "Row 1, left cell" }
       .Set(x => x.Style.TextColor = "red"));
       await MyGrid.Add(new TextView { Text = "Row 1, right cell" });
       await MyGrid.Add(new TextView { Text = "Row 2, left cell" });
       await MyGrid.Add(new TextView { Text = "Row 2, right cell" });
       await MyGrid.Add(new TextView { Text = "Row 3, left cell" });
       await MyGrid.Add(new TextView { Text = "Row 3, right cell" });
```