[vertical]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/stack-class/vertical.png "Zebble-Stack"
[horizontal]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/stack-class/horizontal.png "Zebble-Stack"
[auto]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/stack-class/auto.png "Zebble-Stack"
[alignments]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/stack-class/alignments.png "Zebble-Stack"

### STACK CLASS

The **Stack** class in Zebble allows you to arrange child views either horizontally or vertically next to each other.

#### Vertical Stack

By default, the items will be aligned vertically one after another.

```xml
<Stack>
  <Button BackgroundColor="Blue" Text="A"  />
  <Button BackgroundColor="Green" Text="B"/>
  <Button BackgroundColor="Purple" Text="C" />
</Stack>
```

![vertical]

When you add child views to a stack, it will automatically set their X or Y (depending on the direction of the Stack). 
Also, the height of the stack will keep growing based on the height of its children.
Horizontal Stack
If you want to arrange the items horizontally next to each other, you should set the Direction property to Horizontal.

```xml
<Stack Direction="Horizontal">
  <Button BackgroundColor="Blue" Text="A" />
  <Button BackgroundColor="Green" Text="B" />
  <Button BackgroundColor="Purple" Text="C" />
</Stack>
```

![horizontal]

#### Automatic width

For any view inside a horizontal stack, if it already has a specific width specified, it will be respected. If no width is specified, then the remaining total space will be divided by the number of child views in the stack that have no set width. In the above example, all items have a width of null (auto) and so they all get a third of the total width.

In the next example, two of the boxes have a set width, and the third one is auto, so it takes the rest of the available space:


```xml
<Stack Direction="Horizontal">
  <Button BackgroundColor="Blue" Text="A" Width="60"/>
  <Button BackgroundColor="Green" Text="B" Width="60"/>
  <Button BackgroundColor="Purple" Text="C" />
</Stack>
```

![auto]

Note: To have a specific width, a view does not have to necessarily have its Width property set. It can also be specified in the code behind, CSS or even implicit (such as an image, or auto-width text view). Learn more.

#### Horizontal alignment

If all children inside a horizontal stack have a specific width, then their total sum may be less than the width of the stack (which will come by default from its parent container). In that case, you can decide if the children should be left, center or right aligned by setting the HorizontalAlignment property.

By default, **HorizontalAlignment** is Left. The following example shows how you can set it to Center instead.


```xml
<Stack Direction="Horizontal" HorizontalAlignment="Center">
  <Button BackgroundColor="Blue" Text="A" Width="60"/>
  <Button BackgroundColor="Green" Text="B" Width="60"/>
</Stack>
```

![alignments]