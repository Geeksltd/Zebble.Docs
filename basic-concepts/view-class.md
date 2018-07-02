[viewes]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/view-class/views.png "Zebble-Intro"
[hierarchy]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/view-class/hierarchy.png "Zebble-Intro"
[composition]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/view-class/composition.png "Zebble-Intro"

### VIEW CLASS

There is an abstract class called **View** in Zebble which is the root parent of all Zebble UI objects.

![viewes]

Many other user interface objects in Zebble directly inherit from View for example **Stack** which you see an example of is one example Canvas and other one and there are many components we also have for example an other Abstract Class called TextControl which is something that has TextView and TextInput.

There are a lot of provided and built-in components in Zebble, but you can easily create your own components by inheriting from an View directly or any other subclasses and providing your own functionality. You will able to easily create your custom View Objects. 

It has the following properties:

**Width**, **Height**, **X** and **Y** to define the object's boundaries.

**Padding and Margin:** These are of the type Gap which allows you to set a value for all sides, or each of the sides (left, right, top, bottom) separately.
**Border:** This is of the Border type, allowing you to set the border width and colour for all sides or each side.
 
![hierarchy]

Each View optionally has a parent which is another View and that relationship is children, so that we can have a full hierarchy, so your pages and module typically use this hierarchical structure in order to compose objects together.

![composition]