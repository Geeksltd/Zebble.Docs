[default]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/treeview/default.png "Zebble-TreeView"
[direction]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/treeview/direction.png "Zebble-TreeView"
[indentspace]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/treeview/indentspace.png "Zebble-TreeView"

### TREEVIEW

A TreeView component allows you to show a tree structure that allows expanding or collapsing its nodes.

**Example:**

```xml
<TreeView id="MyTree" />
```
```csharp
var rootNode = await MyTree.AddNode(new TreeView.Node("some text"));
var child = rootNode.Add(new TreeView.Node("child"));
var grandChild = child.Add(new TreeView.Node("grand child"));
```

![default]

#### Adding nodes dynamically:

```csharp
var rootNode = await MyTree.Add(new TreeView.Node("some text");

You can add child nodes to each node to create a full hierarchy.

var child = rootNode.Add(new TreeView.Node("child"));
var grandChild = child.Add(new TreeView.Node("grand child"));
```

#### Automatic Population with IHierarchy

If you have an object which implements IHierarchy interface, then TreeView can populate itself with all of its descendants.

```csharp
IHierarchy myRootObject = ...;
await MyTree.Add(new TreeView.Node(myRootObject));
```

#### Custom view for nodes

Each node in the tree can have a custom view instead of just a text.  For example:

```xsharp
var specialNode = new TreeView.Node { View = new MyCompositionView() };
await MyTree.Add(specialNode);
```

#### IndentSpace

This property value determines the space between left side of component and the location where texts are shown.

```xml
<TreeView Id="MyTree"  IndentSpace="100"/>
```

![indentspace]

#### Direction:

The default value is **Vertical**. When you set it to **Horizontal**, the output shape is :

![direction]

#### Lazy loading

By default, tree views are lazy loaded. This means that when you add a new node to the hierarchy, the actual TextView objects for it will not be created until the user clicks to expand the tree in a way to need to see it. This approach is efficient for large trees.

If you need to use custom views while still benefiting from the lazy loading feature, then instead of the actual view, you should provide a ViewGenerator delegate when creating the node object. For example:

```csharp
var specialNode = new TreeViewNode { ViewGenerator = (node) => new MyCompositionView.... };
```

#### Expanding and collapsing nodes programmatically

Sometimes you need to pre-expand some nodes instead of waiting for the user to manually do it. You can use the node object's Expand() or Collapse() methods for this purpose.

### Events
| Event             | Type                                          | Android | iOS | Windows |
| :-----------      | :-----------                                  | :------ | :-- | :------ |
| on-Flashed            | AsyncEvent    | x       | x   | x       |
| on-Initializing            | AsyncEvent    | x       | x   | x       |
| on-LongPressed            | AsyncEvent    | x       | x   | x       |
| on-PanFinished            | AsyncEvent    | x       | x   | x       |
| on-Panning            | AsyncEvent   | x       | x   | x       |
| on-PreRendered            | AsyncEvent    | x       | x   | x       |
| on-Swiped            | AsyncEvent   | x       | x   | x       |
| on-Tapped            | AsyncEvent    | x       | x   | x       |
