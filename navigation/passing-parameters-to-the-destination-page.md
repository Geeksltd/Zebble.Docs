
### PASSING PARAMETERS TO THE DESTINATION PAGE

If you want to pass parameters to the destination page (e.g. for an Edit form) then you can send as many parameters as you want as an anonymous object:

```csharp
Nav.Go<TargetPage>( { param1 = value2 , param2 = value2 ,...})
```

Then on the target page you can retrieve the parameters using:

```csharp
Nav.Param<T>("param1")
```

**NOTE:** The above methods are also available on Nav.Forward<>() and Nav.ShowPopup<>()