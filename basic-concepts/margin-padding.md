[concept]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/concept.png "Zebble-Margin&Padding"
[margin1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/margin1.png "Zebble-Margin&Padding"
[margin2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/margin2.png "Zebble-Margin&Padding"
[margin3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/margin3.png "Zebble-Margin&Padding"
[margin4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/margin4.png "Zebble-Margin&Padding"
[padding1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/padding1.png "Zebble-Margin&Padding"
[padding2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/padding2.png "Zebble-Margin&Padding"
[padding3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/padding3.png "Zebble-Margin&Padding"
[padding4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/padding4.png "Zebble-Margin&Padding"
[padding5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/margin-padding/padding5.png "Zebble-Margin&Padding"

### MARGIN & PADDING 

#### Margin is related layout concepts:

The Margin property represents the distance between an element and its adjacent elements, and is used to control the element's rendering position, and the rendering position of its neighbors. Margin values can be specified on layout and view classes.

 
![concept]
 

**MarkUp:**

```xml
<... Text="TextView5"  Style.Margin="20"   Style.Border="2" Style.Border.Color="black"/>
```
 
![margin1]
 
```xml
<... Text="TextView6"  Style.Margin.Bottom="50"  Style.Border="2" Style.Border.Color="black"/>
```
 
![margin2]

```xml
<... Text=" TextView7"   Style.Margin.Left="50" Style.Margin.Right="30"  Style.Border="2" Style.Border.Color="black"/>
```
 
![margin3]

```xml
<... Text=" extView8" Style.Margin.Top="50"  Style.Border="2" Style.Border.Color="black"/>
```

![margin4] 

The Padding property represents the distance between an element and its child elements, and is used to separate the control from its own content. Padding values can be specified on layout classes.

**MarkUp:**

```xml
<... Text=" TextView 2" Style.Border ="1" />
```
 
![padding1] 

```xml
<... Text=" TextView 5" Style.Border ="1"  Style.Padding="20" />
```
 
![padding2]


```xml
<... Text=" TextView 6" Style.Border ="1" Style.Padding.Bottom="50"/>
```
 
![padding3]

```xml
<... Text=" TextView 7" Style.Border ="1" Style.Padding.Left="30" />
```
 
![padding4]
 
```xml
<... Text=" TextView 8" Style.Border ="1" Style.Padding.Top="30"/>
```

![padding5]