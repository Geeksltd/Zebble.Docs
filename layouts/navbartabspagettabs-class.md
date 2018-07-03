
### NAVBARTABSPAGE CLASS

This class inherits allows you to have a NavBar at the top, and tabs at the bottom.

The generic type (TTabs) allows your app to have multiple versions of this class, each with different tab sets. This can be useful in some cases where the app is very large, and the tabs are your secondary (as opposed to primary) navigation.

### Why use it?

Just like NavBarPage, the tabs component is shared between different pages that inherit from this page type. This has some benefits:

- Only one version of the tab component is rendered natively.
- Transition between pages is more smooth.
- The tabs component stays fixed positioned and stays out of the transition animations.

#### Location of the tabs

By default the location of the Tabs component is at the bottom for Windows and iOS, and at the top for Android.

If you want to customise this behaviour you can set the boundaries of the following in your PreRender() code:

- Tabs component
- The page content container (BodyScroller)