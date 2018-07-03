[fullpath]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/c-methods-and-peroperties-of-ui/fullpath.png "Zebble-UIMethods"
[round]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/c-methods-and-peroperties-of-ui/round.png "Zebble-UIMethods"
[filepicker]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/c-methods-and-peroperties-of-ui/filepicker.png "Zebble-UIMethods"

### C# METHODS AND PROPERTIES OF UI COMPONENTS

#### Common Properties
ActualHeight and actualWidth:

When you do not set Height and Width properties of any component, in runtime, the its value is zero. In this situation, you should work with ActualHeight or ActualWidth.

On the other hand, if you determine Height and Width properties, the values of Height and ActualHeight are same.

Other properties, ActualBottom, ActualRight are same.

#### IsShown:

If an object is visible, This property is true.

#### NativeHeight & NativeWidth:

The value of NativeHeight is equal to Height, and The value of NativeWidth is equal to Width.

#### Parent:

The value of this property is the container of the object. The default value is Stack #body.

#### ShouldLazyLoad:

If you want to use LazyLoading feature and the component supports that, you should set this property to true. The default value is false.

#### Common Methods

**Add:**

If you want to add an object to the special object such as special Stack, you can use this method.

```csharp
stack1.Add(MyButton1);
```

**AvoidAutoHeight:**

If you want to prevent users to change the height of an object, you could call this method.

**BringToFront:**

The control is moved to the front of the z-order. If the control is a child of another control, the child control is moved to the front of the z-order. BringToFront does not make a control a top-level control.

**GetFullPath:**

You can fetch the full path of an object as following:

```csharp
Task SomethingTapped() => Alert.Show(MyButton1.GetFullPath().ToString());
```

![fullpath]

**Round:**

This method caused the object to round all corners of it.

```csharp
MyButton1.Round();
```

![round]

**SendToBack:**

The control is moved to the back of the z-order. If the control is a child of another control, the child control is moved to the back of the z-order. If the control is a top-level control, this method will not work correctly unless the control is active. A top-level control is a control, such as a Form, that is not a child of another control. An active control is a visible control that has input focus. To use the SendToBack method with an inactive, top-level control, first call the BringToFront method on the control.

#### Carousel

**AddSlide():**

If you want to add a slide in runtime, you can use this method.

```csharp
MyCarousel.AddSlide(View);
```

**Next():**

By using this method, you can change the current slide to the next one.

**Previous():**

By using this method, you can change the current slide to the previous one.

 

#### FilePicker
Button.Text:

You can set the text of FilePicker by give value to this property.

```csharp
MyFilePicker.Button.Text = "Select ...";
```

![filepicker]

**File:**

This property returns the selected file attributes.

It has all properties such as DirectoryName, Name, length , ... .

**AllowOnly():**

This method sets which types of files could be allowed to select by user.

**PickPhoto():**

This method shows PickPhoto feature.

**PickVideo():**

This method shows PickVideo feature.

**TakePhoto():**

This method shows TakePhoto feature.

**TakeVideo():**

This method shows TakeVideo feature.


#### TextInput

**IsFocused:**

When the object gets the focus, this property is set to true. The default value is false.

 

#### WebView

**SetHtml():**

You can change the Html content of WebView by using this function.

**SetUrl():**

You can change the Url link of WebView by using this function.