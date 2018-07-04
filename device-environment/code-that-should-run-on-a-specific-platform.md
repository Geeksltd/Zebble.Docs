
### CODE THAT SHOULD RUN ON A SPECIFIC PLATFORM

If you want to write a conditional logic to run a piece of code for specific platform only, you can query the CURRENT platform using the following:

```csharp
if (Device.Platform == DevicePlatform.IOS)
{
       ........
}
```