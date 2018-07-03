
### FLASHING ON TAP USING AUTOFLASH

Imagine you have a button that does something when it's tapped. The action of that button may happen very quickly or it may take a little while. Therefore, the user may not see an immediate feedback when tapping a button, leading them to tap it again multiple times, or feel like the app isn't very responsive.

**To avoid that problem, a good UX practice is to always show an immediate feedback to the user when a button (or any view that does something) is tapped.**

#### AutoFlash attribute

All views in Zebble have a boolean attribute named AutoFlash which can be set to true or false. You can set it to true for any other object. For example:

```xml
<ImageView on-Tapped="...." AutoFlash="true" />
```

For Button and IconButton types, it's set to the config value of **"Button.Tap.AutoFlash"**. 

When AutoFlash is set to true, an event handler will be added to the view's Tapped event to invoke the Flash() method.

#### Flash() method

Every view in Zebble has a Flash() method. The effect of what a flash means can be customized by handling its **Flashed** event.

If the event is not handled, then by default:

- The opacity of the object will be set to 50% and then animated back to normal.
- If it's a list view item, then in addition to the above, its background will be set to light grey too.

This effect is often safe in terms of UI and can provide an immediate feedback to let the user know that the tap event has been recognised and it's being executed. It makes the app feel more responsive and prevent multiple taps.

#### Important note: undoing flash

Other than Flashing, sometimes you might want to apply a visual change on a view that you will then shortly undo. A typical example is emphasisng an object by changing its size, border, etc. In such cases you must preserve the previous state of the view's Css as well as Style and reapply it after your change. You can achieve that using the following pattern:

```csharp
protected virtual async Task ApplyDefaultFlash()
{
    // this creates a snapshot of both Css.Opacity and Style.Opacity value.
    var state = Stylesheet.Preserve(this, x => x.Opacity);

    // Now apply any changes that you want on Opacity of the object.
    await this.Animate(Animation.FlashDuration, x => x.Opacity(0.5));

    // Then call Reverse() to set both Css.Opacity and Style.Opacity back to their original values.
    state.Reverse();
}
```

Or you can use the following shorter version using the Disposable pattern:

```csharp
protected virtual async Task ApplyDefaultFlash()
{
       using (Stylesheet.Preserve(this, x => x.Opacity))
       {
             await this.Animate(Animation.FlashDuration, x => x.Opacity(0.5));
       }
}
```