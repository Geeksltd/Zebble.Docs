
### SUPPORTED SELECTORS

All of the following selectors and any combination of them is supported:

#### Direct selectors

```css
ElementType { ... }

SomeClass-NestedClass { ... }

.class-name { ... }

#ElementId { ... }

ElementType#SomeID { ... }

ElementType.some-class { ... }

.class1.class2 { ... }

#SomeID.with-class { ... }

etc
```

#### Nesting (space seperated)

```css
ParentSelector .child-selector { ... }

ParentSelector .child-selector #GrandChildSelector { ... }

ParentSelector > .direct-children-only
```

#### Whild card

```css
ParentSelector * { ... }
```

#### Combinations

```css
Selector1 , Selector 2 { ... }
```