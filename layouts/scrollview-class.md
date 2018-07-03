[sample1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/scrollview-class/sample1.gif "Zebble-Stack"
[sample2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/scrollview-class/sample2.gif "Zebble-Stack"

### SCROLLVIEW CLASS

As the name implies, a scroll view is a container that scrolls its children.

```xml
<ScrollView Id="Scoller">
 ... body here...
</ScrollView>
```
 
![sample1]
 

**Sample:**

```xml
<ScrollView>
      <ImageView Path="Images/p1.jpg" />
      <ImageView Path="Images/p2.jpg" />
      <ImageView Path="Images/p3.jpg" />
</ScrollView>
```

#### Properties:

- **Direction:** By default it's Vertical. You can set it to Horizontal if you need.
- **PagingEnabled:** When set to true, the user's scrolling will snap based on the size of the scroll view itself. This is useful to create a carousel effect.
- **PartialPagingEnabled | PartialPagingSize:** When enabled, then when the user is scrolling the content, it will snap according to the specified size. This is useful for creating an effect similar to Month Rotator in a date picker.
- **ScrollX, ScrollY:** These allow you to read or set current scroll position.
- **EnableScrolling:** When set to false, freezes additional scrolling.

#### Events:

- **ContentSizeChanged:** Raised when the contents of a scroll view are changed in a way to cause a change in their total size.
- **EnableScrollingChanged:** Raised when the scrolling ability of a scroll view is changed to Enable or Disable.
- **OnePagePartialPagingEnabled:** Raised when the PartialPaging of a scroll view is changed.
- **Flashed:** Raised when the scroll view is flashed.
- **Initialized:** Raised when the scroll view object is created and rendered.
- **Initializing:** Raised when the scroll view object is being created and rendered.
- **LongPressed:** Raised when user clicked on the scroll view for a long time.
- **PanFinished:** Raised when user panned on the scroll view.
- **Panning:** Raised when user starts to pan on the scroll view.
- **PreRendered:** Raised when the scroll view object is not started to rendered before rendering.
- **RefreshScrollContentSize:** Raised when the size of contents of a scroll view are changed.
- **ScrolledToNewPage:** Raised when the new page of scroll view is shown.
- **ScrollEnded:** Raised when a scrolling action is completed.
- **Swiped:** Raised when user swiped on the scroll view.
- **Tapped:** Raised when user tapped on the scroll view.
- **UserScrolledHorizontally:** Raised when user scrolled the scroll view object horizontally.
- **UserScrolledVertically:** Raised when user scrolled the scroll view object horizontally.
- **UserZoomChanged:** Raised when user zooms the scroll view object.

#### Zooming

Scrollview allows you to make your content zoomable. For example, you can place an image inside such a scroll view to allow the user to zoom into the image and move it around.

```xml
<ScrollView EnableZooming="true">
    <ImageView ..../>
</ScrollView>
```

**Sample:**

```xml
<ScrollView EnableZooming="true">
      <ImageView Path="Images/p1.jpg" />
      <ImageView Path="Images/p2.jpg" />
      <ImageView Path="Images/p3.jpg" />
</ScrollView>
```

![sample2]