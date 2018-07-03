[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/navigation/waiting-class/1.gif

### WAITING CLASS

If you have a long-running operation you can show the waiting indicator animation using the following code:

![1]

```csharp
async Task MyButtonTapped()
{
        await Waiting.Show();
        // Now Invoke long-running task
        await Waiting.Hide();
}
```