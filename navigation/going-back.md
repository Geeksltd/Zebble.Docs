[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/navigation/going-back/1.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/navigation/going-back/2.png

### GOING BACK

The standard practice in iOS is to use NavBar to show a **software back button**. In Android and Windows phone you have a **hardware back button** that show always work, but you have also an option to show a software back button.

![1] 

In this example, the home page on the left hand side shows the root pages. When we click on the first root page which is General, you can see the back button on the top-left side of the General page.

The Nav Class is in Zebble has a static property called CurrentPage which always return to page that users looking at. The result is a Stack property which holds the pages in the current history. So that you can enable going back:

![2]

You can use any of the following methods to go back to another page.

```csharp
// This will go back to the last item on the stack.
// If there is nothing on the stack it throws an exception.
Nav.Back();

// This will go to the specified page and clear the stack (similar to Go() method).​
Nav.GoBack<TargetPage>()
```

The difference between this and Nav.Go() is that when you go to a target page with GoBack() the animation transition will be the **reverse of the animation** with which the user came to the current page.

For example if the user came to the current page with SlideForward, then the transition used for going to the TargetPage of GoBack() will be SlideBack.