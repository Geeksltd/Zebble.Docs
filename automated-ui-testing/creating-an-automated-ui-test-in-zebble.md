
### CREATING AN AUTOMATED UI TEST IN ZEBBLE

#### Creating a UI Test project

Add the NuGet package of Zebble.UITesting to your solution.<br>
Add a new shared project to your solution named "UITests".<br>
Add a reference to the shared project from your platform specific projects (UWP, Android, iOS)<br>

In UWP\Program.cs update the Main() method:

```csharp
public static void Main(string[] args)
{
     Zebble.UITesting.TestRunner.Initialize(args);
     // ... the rest as what it was.
}
```

In Startup.cs file, change the LoadFirstPage() method to the following:

```csharp
public static async Task LoadFirstPage()
{
     await Nav.Go(new Pages.MyStartPage());       
     await Zebble.UITesting.TestRunner.Run();
}
```

#### Creating a test 

In your UITests project add a test class. Name it after the scenario that you want to test, for example "ManageContacts". It should inherit from TestScenario in Zebble.UITesting namespace and implement the Run() method.

```csharp
namespace UITests
{
    using System;
    using Zebble.UITesting;
    using System.Threading.Tasks;

    class ManageContacts : TestScenario
    {
        public override void Run()
        {
            Tap("Contacts");
            ExpectHeader("Contacts");

            // Test adding a contact:
            Tap("Add");
            Set("First name").To("Jack");
            Set("Last name").To("Williams");
            Tap("Save");
            Expect("Jack Williams");

            // Test deleting a contact
            AtRow("Jack Williams").Swipe(SwipeDirection.Left);
            AtRow("Jack Williams").Tap("Delete");
            ExpectNo("Jack Williams");
        }
    }
}
```

#### UI Testing Commands

You can invoke any of the following commands as part of your test script:


- Tap("my button")
- Set("some field").To("some value")
- ...

#### Locators and Context 

Often you can have several objects on the screen with the same text. To resolve ambiguity, you can use one or a combination of location specifiers from the following list:

- Near("something")
- Above("something")
- ...