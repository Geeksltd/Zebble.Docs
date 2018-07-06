[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/3-1.png
[2]:https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/3-2.png
[3]:https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/3-3.png
[4]:https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/3-4.png
[5]:https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/3-5.png

### CREATING TASK LIST IN ZEBBLE

If you do not install Zebble in your Visual Studio, please first check out [Install Zebble in Visual Studio](http://zebble.net/docs/preparing-visual-studio-for-installing-zebble) topic.

 ![1]

In every Zebble project there are some important files which will be explained briefly. First type of files are zbl files.
**zbl** files are XML files by nature. They are user interface files. You can, also, create user interface in c#.
As you can see in the picture below in **“App.UI”**, we have Page1.zbl which we want to be our first page.

To tell the project to start from page1 you should do the following steps:

![2]
 
Go to the “StartUp” file.

In this file you should change **“LoadFirstPage”** file to Page1.

```csharp
public static Task LoadFirstPage() => Nav.Go(new Pages.Page1());
Now the Zebble project knows that it should start from Page1.
```
 
This is Page1:

```xmml
<?xml version="1.0" encoding="utf-8" ?>
<z-Component z-type="Page1" z-base="NavBarPage" z-namespace="UI.Pages" Title="My Task List"
    z-partial="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
</z-Component>
```

The result will be like this:

 
![3]
 

First, let us add a **“DatePicker”** and a **“Button”**. Before doing that, we need to create a stack element and add the
aforementioned elements to the stack. A stack allows us to arrange items either vertically or horizontally. By default,
the direction is vertical. Adding the “DatePicker” and the “Button” is, as you can see in the picture, pretty
straightforward.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<z-Component z-type="Page1" z-base="NavBarPage" z-namespace="UI.Pages" Title="My Task List"
    z-partial="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
<!--Adding a date picker and an add button vertically-->
<Stack Id="Date_Add" Style.Margin.Top="80">
    <DatePicker Id="MyDatePicker"/>
    <Button Id="MyButton" text="Add a task!" Style.Border="4" Style.Border.Color="green" />
</Stack>
</z-Component>
```

The result can be seen in the following picture:

![4]

We will add event handler for the Button later. Now let’s add a “ListView” below the Button. To do this, we will add a **Zebble|ListModule** to our project pages.

Now you need to change some lines in MyList1.zbl and MyList1.zbl.cs. In MyList1.zbl apply these changes:

```xml
<?xml version="1.0" ?>
<z-Component z-type="MyList1" z-base="Stack" z-namespace="UI.Modules"
    z-partial="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
<ListView z-of="string, Row" Id="List" DataSource="Items">
<z-Component z-type="Row" z-partial="true" z-base="ListViewItem[string]" AutoFlash="true"" on-Tapped="RowTapped">
<!--######### DESIGN YOUR LIST ITEM TEMPLATE HERE ############-->
<TextView Id="Name" CssClass="title" Text="@Item.ToString()" />
<imageView Id="ViewButton" CssClass="view-row" Path="Images/Icons/Arrow-Right.png" />
<!--######### NEED SLIDE-IN BUTTONS? ############-->
<z-place inside="SlideIn">
    <Button Text="Hello!" />
</z-place>
</z-Component>
</ListView>
</z-Component>
```

In MyList1.zbl.cs:

```csharp
partial class myList1
{
    List<string> Items;
    public override async Task OnInitializing()
    {
        //TODO: Load your data source.
        Items = new List<string> { "Example 1", "Example 2", "Example 3", "Example 4", "..." };
        await base.OnInitializing();
        await InitializeComponent();
    }
}
```

Now let’s add a ListView to page1:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<z-Component z-type="Page1" z-base="NavBarPage" z-namespace="UI.Pages" Title="My Task List"
    z-partial="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
<!--Adding a date picker and an add button vertically-->
<Stack Id="Date_Add" Style.Margin.Top="80">
    <DatePicker Id="MyDatePicker"/>
    <Button Id="MyButton" text="Add a task!" Style.Border="4" Style.Border.Color="green" />
    <UI.Modules.MyList1 />
</Stack>
</z-Component>
```
 
Running the project will give us something like this:

![5] 

Finally, let’s add a delete and a done button which can be seen when the user swipe left. The “Delete” button
is red and the “Done” button is green:

```xml
<?xml version="1.0" ?>
<z-Component z-type="MyList1" z-base="Stack" z-namespace="UI.Modules"
    z-partial="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="./../.zebble-schema.xml">
<ListView z-of="string, Row" Id="List" DataSource="Items">
<z-Component z-type="Row" z-partial="true" z-base="ListViewItem[string]" AutoFlash="true"" on-Tapped="RowTapped">
<!--######### DESIGN YOUR LIST ITEM TEMPLATE HERE ############-->
<TextView Id="Name" CssClass="title" Text="@Item.ToString()" />
<imageView Id="ViewButton" CssClass="view-row" Path="Images/Icons/Arrow-Right.png" />
<!--######### NEED SLIDE-IN BUTTONS? ############-->
<z-place inside="SlideIn">
    <Button Text="Done" Style.BackgroundColor="green"/>
    <button Text="delete" Style.BackgroundColor="red" />
</z-place>
</z-Component>
</ListView>
</z-Component>
```