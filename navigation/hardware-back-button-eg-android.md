
### HARDWARE BACK BUTTON (E.G. ANDROID)

Some devices such as Android and Windows Phone have a hardware or operating system "back" button. When it's pressed, the **Nav.HardwareBack** event gets fired. You can handle this static event for any custom handling. By default, Zebble will take the user back to the previous page in the Navigation Stack.

**Example:**

```csharp
public class StartUp : Zebble.StartUp
{
     public override async Task Run()
     {
          ....
          Nav.HardwareBack.Handle()
     }    

    async Task OnHardwareBackPressed(System.ComponentModel.CancelEventArgs args)   
    {
        if (Nav.Stack.Any()) return; // Allow the normal behaviour

        if (!await Alert.Confirm("Do you want to close the app?"))
           args.Cancel = true; // Setting Cancel to true will prevent the standard system behaviour
    }
}
```

#### Testing the Back button during development

You can actually test the button in the UWP version.

- On any page, use Ctrl + Click on the page to launch the Designer window.
- On the top right corner, you can see a button reading "Back".
- You can press that button to simulate the device back button.

#### Close the app with Hardware Back button?

When the user is looking at a page while there is no previous page in the navigation stack, if she then presses the back button nothing will happen.

In that scenario, if you want the application to be minimised to show the Android home page, then you can achieve that behaviour by setting the following in your **Config.xml** file.

```xml
<Android.Hardware.Back.Can.Close>true</Android.Hardware.Back.Can.Close>
```