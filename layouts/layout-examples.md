[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/1.png "Zebble-Layout"
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/2.png "Zebble-Layout"
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/3.png "Zebble-Layout"
[4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/4.png "Zebble-Layout"
[5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/5.png "Zebble-Layout"
[6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/6.png "Zebble-Layout"
[7]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/7.png "Zebble-Layout"
[8]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/8.png "Zebble-Layout"
[9]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/9.png "Zebble-Layout"
[10]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/10.png "Zebble-Layout"
[11]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/11.png "Zebble-Layout"
[12]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/12.png "Zebble-Layout"
[13]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/13.png "Zebble-Layout"
[14]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/14.png "Zebble-Layout"
[15]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/15.png "Zebble-Layout"
[16]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/16.png "Zebble-Layout"
[17]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/17.png "Zebble-Layout"
[18]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/18.png "Zebble-Layout"
[19]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/19.png "Zebble-Layout"
[20]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/layout-examples/20.png "Zebble-Layout"

### LAYOUT EXAMPLES

#### Sample 1:

![1]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
    <Stack Direction="Horizontal">
        <TextView Text="3" CssClass="box left" />
        <TextView Text="4" CssClass="box middle" />
        <TextView Text="5" CssClass="box right" />
    </Stack>
    <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue }
.footer { background: orange; }
.left { background: green; }
.middle { background: brown; }
.right { background: purple; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its three direct children (rows) are automatically positioned each at the correct Y position one after another.
- The middle child is itself a horizontal stack. So its children (3, 4 and 5) are automatically positioned next to each other with the correct X.
- No explicit Width is specified for any object. So they each take as much width as they can. For 1 and 2 this means 100% of the parent. For 3, 4 and 5, they take an equal share of the available container's space.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (3, 4 and 5) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 300px (100px for 1, 100px for 2 and 100px for the horizontal stack).

#### Sample 2:

![2]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<TextView Text="4" CssClass="box middle" />
<TextView Text="5" CssClass="box right" />
</Stack> <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; } .footer { background: orange; }
.left { background: green; width: 25%; }
.middle { background: brown; width: 50%; }
.right { background: purple; width: 25%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its three direct children (rows) are automatically positioned each at the correct Y position one after another.
- The middle child is itself a horizontal stack. So its children (3, 4 and 5) are automatically positioned next to each other with the correct X.
- There are explicit Width for each child. For 1 and 3 this means 25% of the parent. For 4 this means 50% of the parent.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (3, 4 and 5) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 300px (100px for 1, 100px for 2 and 100px for the horizontal stack).

#### Sample 3:

![3]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<TextView Text="4" CssClass="box right" />
</Stack> <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.footer { background: orange; }
.left { background: green; width: 50%; }
.right { background: purple; width: 50%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its three direct children (rows) are automatically positioned each at the correct Y position one after another.
- The middle child is itself a horizontal stack. So its children (3 and 4) are automatically positioned next to each other with the correct X.
- There are explicit Width for each child and it means 50% of the parent for each one.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (3 and 4) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 300px (100px for 1, 100px for 2 and 100px for the horizontal stack).

#### Sample 4:

![4]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<TextView Text="4" CssClass="box right" />
</Stack> <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.footer { background: orange; }
.left { background: green; width: 30%; }
.right { background: purple; width: 70%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its three direct children (rows) are automatically positioned each at the correct Y position one after another.
- The middle child is itself a horizontal stack. So its children (3 and 4) are automatically positioned next to each other with the correct X.
- There are explicit Width for each child. For 3 and 4 these mean 30% and 70% of the parent respectively.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (3 and 4) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 300px (100px for 1, 100px for 2 and 100px for the horizontal stack).

#### Sample 5:

![5]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<TextView Text="4" CssClass="box right" />
</Stack> <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.footer { background: orange; }
.left { background: green; width: 70%; }
.right { background: purple; width: 30%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its three direct children (rows) are automatically positioned each at the correct Y position one after another.
- The middle child is itself a horizontal stack. So its children (3 and 4) are automatically positioned next to each other with the correct X.
- There are explicit Width for each child. For 3 and 4 these mean 70% and 30% of the parent respectively.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (3 and 4) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 300px (100px for 1, 100px for 2 and 100px for the horizontal stack).

#### Sample 6:

![6]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box topleft" />
<TextView Text="4" CssClass="box topmiddle" />
<TextView Text="5" CssClass="box topright" />
</Stack> <Stack Direction="Horizontal">
<TextView Text="6" CssClass="box downleft" />
<TextView Text="7" CssClass="box downmiddle" />
<TextView Text="8" CssClass="box downright" />
</Stack> <TextView Text="2" CssClass="box footer" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.footer { background: orange; }
.topleft { background: green; width: 34%; }
.topmiddle { background: brown; width: 32%; }
.topright { background: purple; width: 34%; }
.downleft { background: silver; width: 34%; }
.downmiddle { background: gold; width: 32%; }
.downright { background: gray; width: 34%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its four direct children (rows) are automatically positioned each at the correct Y position one after another.
- The second and third children are themselves three horizontal stacks. - So the children of second row (3, 4 and 5) and the children of third row (6, 7 and 8) are automatically positioned next to each other with the correct X.
- There are explicit Width for each child. The left, middle and third child have 34%, 32% and 34% of parent respectively.
- The Height of all text views is explicitly set as 100px.
- The Height of the middle rows (horizontal stacks) are determined by their tallest direct child which is 100px as in this case all their children (3,4,5,6,7 and 8) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 400px (100px for 1, 100px for 2 and 200px for the horizontal stacks).

#### Sample 7:

![7]

**In markup:**

```xml
<Stack> <Stack Direction="Horizontal">
<TextView Text="1" CssClass="box topleft" />
<TextView Text="2" CssClass="box topmiddle" />
<TextView Text="3" CssClass="box topright" />
</Stack> <Stack Direction="Horizontal">
<TextView Text="4" CssClass="box downleft" />
<TextView Text="5" CssClass="box downmiddle" />
<TextView Text="6" CssClass="box downright" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.topleft { background: green; width: 34%; }
.topmiddle { background: brown; width: 32%; }
.topright { background: purple; width: 34%; }
.downleft { background: silver; width: 34%; }
.downmiddle { background: gold; width: 32%; }
.downright { background: gray; width: 34%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are horizontal stack and automatically positioned each at the correct Y position one after another in each row.
- First row has itself three textview (1,2 and 3) which have explicit Width 34%, 32% and 34% respectively and they are automatically positioned next to each other with the correct X.
- Second row has itself three textview (4,5 and 6) which have explicit Width 34%, 32% and 34% respectively and they are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the each row (horizontal stack) is determined by their tallest direct child which is 100px as in this case all their children have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px for the horizontal stacks.

#### Sample 8:

![8]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box middle" />
<TextView Text="4" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.left { background: green; width: 34%; }
.middle { background: brown; width: 32%; }
.right { background: purple; width: 34%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2, 3 and 4) are automatically positioned next to each other with the correct X.
- Each child of second row has explicit Width 34%, 32% and 34% respectively and they are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the second row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (2, 3 and 4) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px (100px for 1, 100px for the horizontal stack).

#### Sample 9:

![9]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box middle" />
<TextView Text="4" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.left { background: green; width: 34%; }
.middle { background: brown; width: 32%; }
.right { background: purple; width: 34%; }

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2, 3 and 4) are automatically positioned next to each other with the correct X.
- Each child of second row has explicit Width 34%, 32% and 34% respectively and they are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the second row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (2, 3 and 4) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px (100px for 1, 100px for the horizontal stack).

#### Sample 10:

![10]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.left { background: green; width: 30%; }
.right { background: purple; width: 70%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2 and 3) are automatically positioned next to each other with the correct X.
- Each child of second row has explicit Width 30%, 70% respectively and they are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the second row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (2 and 3) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px (100px for 1, 100px for the horizontal stack).

#### Sample 11:

![11]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; } .left { background: green; width: 70%; }
.right { background: purple; width: 30%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2 and 3) are automatically positioned next to each other with the correct X.
- Each child of second row has explicit Width 70%, 30% respectively and they are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the second row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (2 and 3) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px (100px for 1, 100px for the horizontal stack).

#### Sample 12:

![12]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; } .left { background: green; width: 50%; }
.right { background: purple; width: 50%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2 and 3) are automatically positioned next to each other with the correct X.
- Each child of second row has explicit Width that is equal to 50% of its parent. They are automatically positioned next to each other with the correct X.
- The Height of all text views is explicitly set as 100px.
- The Height of the second row (horizontal stack) is determined by its tallest direct child which is 100px as in this case all its children (2 and 3) have 100px.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px (100px for 1, 100px for the horizontal stack).

#### Sample 13:

![13]

**In markup:**

```xml
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<Stack> <TextView Text="1" CssClass="box header" />
<TextView Text="2" CssClass="box footer" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; }
.header { background: blue; height:20%; }
.footer { background: orange; height:80% }
.left { background: green; width: 20%; height:200px; }
```

**Elaboration of rendering logic:**

- The root container is a HORIZONTAL stack. So its two direct children (columns) are automatically positioned each at the correct X position one after another.
- The first child is itself a text view (3) and its explicit width is 20% of parent. So second child takes as much width as it can (80%).
- The second child is itself a vertical stack. So its children (1 and 2) are automatically positioned next to each other with the correct Y.
- Each child of second column has explicit height 20%, 80% respectively and they are automatically positioned next to each other with the correct Y.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px.

#### Sample 14:

![14]

**In markup:**

```xml
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<Stack> <TextView Text="1" CssClass="box header" />
<TextView Text="2" CssClass="box footer" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; }
.header { background: blue; height:20%; }
.footer { background: orange; height:80% }
.left { background: green; width: 100px; height:200px; }
```

**Elaboration of rendering logic:**

- The root container is a HORIZONTAL stack. So its two direct children (columns) are automatically positioned each at the correct X position one after another.
- The first child is itself a text view (3) and its explicit width is equal to 100px. So second child takes as much width as it can.
- The second child is itself a vertical stack. So its children (1 and 2) are automatically positioned next to each other with the correct Y.
- Each child of second column has explicit height 20%, 80% respectively and they are automatically positioned next to each other with the correct Y.
- The Height of the root object (vertical stack) is determined by the sum of its children, which is 200px.

#### Sample 15:

![15]

**In markup:**

```xml
<Stack Direction="Horizontal">
<TextView Text="3" CssClass="box left" />
<Stack> <TextView Text="1" CssClass="box header" />
<TextView Text="2" CssClass="box footer" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; }
.header { background: blue; height:50px; }
.footer { background: orange; height:100px; width:100%; }
.left { background: green; width: 50px; height:150px; }
```

**Elaboration of rendering logic:**

- The root container is a HORIZONTAL stack. So its two direct children (columns) are automatically positioned each at the correct X position one after another.
- The first child is itself a text view (3) and its explicit width is equal to 50px and its height is 150px. So second child takes as much width as it can.
- The second child is itself a vertical stack. So its children (1 and 2) are automatically positioned next to each other with the correct Y.
- First child of second column has explicit height 50px and second one has explicit height 100px. So the height of the root is sum of them (100+50) and is equal to 150px. 

#### Sample 16:

![16]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box left" />
<TextView Text="3" CssClass="box right" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height:150px;}
.header { background: blue; height:50px;}
.left { background: green; width: 20%; }
.right { background: purple; width: 80%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack. So its two direct children (rows) are automatically positioned each at the correct Y position one after another.
- The first child is itself a text view (1).
- The second child is itself a horizontal stack. So its children (2 and 3) are automatically positioned next to each other with the correct X.
- The width of second row is 150px.
- The Height of the root is sum of 1 and 2. So it is equal to 150+50= 200px.

#### Sample 17:

![17]

**In markup:**

```xml
<Stack Direction="Horizontal">
<Stack> <TextView Text="1" CssClass="box header" />
<TextView Text="2" CssClass="box footer" />
</Stack> <TextView Text="3" CssClass="box right" />
</Stack>
````

**In Css:**

```css
.box { color: white; text-align: center; }
.header { background: blue; height:20%; }
.footer { background: orange; height:80% }
.right { background: purple; width: 20%; height:200px; }
```

**Elaboration of rendering logic:**

- The root container is a HORIZONTAL stack. So its two direct children (columns) are automatically positioned each at the correct Y position one after another.
- The root container does not have the explicit size and the size of it is related to its children. Its height is equal to second column(3) that is 200px.
- The first child is itself a vertical stack and its explicit height is equal to 20% of container. It means 20% of 200px. So second child takes as much width as it can.
- The Height of the root object (vertical stack) is determined by the text view, which is 200px.
- The height of The second child of first column(2) is 80% of 200px.

#### Sample 18:

![18]

**In markup:**

```xml
<Stack Direction="Horizontal">
<Stack> <TextView Text="1" CssClass="box header" />
<TextView Text="3" CssClass="box middle" />
<TextView Text="2" CssClass="box footer" />
</Stack> <TextView Text="4" CssClass="box right" />
</Stack>
```

**In Css:**

```css
.box { color: white; text-align: center;}
.header { background: blue; height:20%; }
.middle { background: brown; height:60%; }
.footer { background: orange; height:20% }
.right { background: green; width: 20%; height:200px; }
```

**Elaboration of rendering logic:**

- The root container is a HORIZONTAL stack. So its three direct children (columns) are automatically positioned each at the correct Y position one after another.
- The root container does not have the explicit height size and the size of it is related to its children. Its height is equal to second column(3) that is 200px.
- The first child is itself a vertical stack and its explicit height is equal to 20% of container. It means 20% of 200px. Meanwhile, the second child(3) takes 60% of 200px and then the last child(2) takes 20% of 200px.
- The Height of the root object (vertical stack) is determined by the text view(4), which is 200px.
- The height of The second child of first column(2) is 80% of 200px.

#### Sample 19:

![19]

**In markup:**

```xml
<Stack> <Stack Direction="Horizontal">
<TextView Text="1" CssClass="box topleft" />
<TextView Text="2" CssClass="box topright" />
</Stack> <Stack Direction="Horizontal">
<TextView Text="3" CssClass="box downleft" />
<TextView Text="4" CssClass="box downmiddle" />
<TextView Text="5" CssClass="box downright" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.topleft { background: green; width: 50%; }
.topright { background: purple; width: 50%; }
.downleft { background: silver; width: 34%; }
.downmiddle { background: gold; width: 32%; }
.downright { background: gray; width: 34%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack and it has two horizontal nested stacks.
- The first nested stack includes two direct children (1 and 2) are automatically positioned each at the correct X position one after another. The height of it is 100px.
- The second nested stack includes three direct children (3, 4 and 5) are automatically positioned each at the correct X position one after another.The height of it is 100px.
- The root container has the explicit height size and the size of it is 200px, because each row is 100px.
- In terms of first row, the first child(1) has 50% of container for its width. So the measure is equal to half of container. The second one(2) is too.
- In terms of second row, the first child has 34% of container for its width. The second one is 32% and the third one is 34%.
- The width of the root object (vertical stack) is determined by the container width.

#### Sample 20:

![20]

**In markup:**

```xml
<Stack> <TextView Text="1" CssClass="box header" />
<Stack Direction="Horizontal">
<TextView Text="2" CssClass="box topleft" />
<TextView Text="3" CssClass="box topright" />
</Stack> <Stack Direction="Horizontal">
<TextView Text="4" CssClass="box downleft" />
<TextView Text="5" CssClass="box downmiddle" />
<TextView Text="6" CssClass="box downright" />
</Stack> </Stack>
```

**In Css:**

```css
.box { color: white; text-align: center; height: 100px; }
.header { background: blue; }
.topleft { background: green; width: 50%; }
.topright { background: purple; width: 50%; }
.downleft { background: silver; width: 34%; }
.downmiddle { background: gold; width: 32%; }
.downright { background: gray; width: 34%; }
```

**Elaboration of rendering logic:**

- The root container is a vertical stack and it has a text view and two horizontal nested stacks.
- The text view height is 100px.
- The first nested stack(second row) includes two direct children (2 and 3) are automatically positioned each at the correct X position one after another. The height of it is 100px.
- The second nested stack(third row) includes three direct children (4, 5 and 6) are automatically positioned each at the correct X position one after another.The height of it is 100px.
- The root container has the explicit height size and the size of it is 300px, because each row is 100px.
- In terms of first row, the first child(1) has 100% of container for its width.
- In terms of second row, the first child has 50% of container for its width. The second one is 50%.
- In terms of second row, the first child has 34% of container for its width. The second one is 32% and the third one is 34%.
- The width of the root object (vertical stack) is determined by the container width.