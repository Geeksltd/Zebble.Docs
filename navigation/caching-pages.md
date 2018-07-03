
### CACHING (PAGES)

A very effective way to make your apps faster is by caching the pages where possible. You can achieve that in Zebble via either of the following methods:

In the code behind of your Zebble page, add [CacheView] attribute:

```csharp
[CacheView]
partial class MyPage
{
   ....
}
```

Or, in the ZBL markup, add `z-cache="true"`:

```xml
<z-Component z-type="MyPage" .... z-cache="true">
   ...
</z-Component>
```

#### How is it used in Zebble?

Normally when you **navigate away from** a page, it is disposed of by the system as soon as it gets a chance (usually in less than a second after leaving the page).

When you enable caching for a page, it will no longer be disposed of when navigating away from that page. Instead, it will remain inside a static stack in the Nav class.

When you navigate to a page, if it does not exist in the cache, it will be created and rendered before the page transition animation starts. If it does exist in the cache, however, then the previously created and rendered page will be displayed and the transition animation will start immediately.

#### Cached page lifecycle

The standard view lifecycle events such as OnInitializing, OnInitialized, OnPreRender, OnApplyingStyle, etc are only invoked when a page is created for the first time. If you navigate back to a page that was previously cached, those events will not be fired.

The only event that will be fired is the **Shown** event, which you can handle by using the WhenShown(...) method.

#### Caching v.s. Nav parameters

For each cached page, there will be a maximum of one instance created and used by the Nav cache management system. If your cached page doesn't use any navigation parameters, then everything is fine. For example:

```csharp
await Nav.Go<ACachedPage>();
```

But how about when you navigate to a cache-able page that accepts a parameter? Consider a cache-able page that shows the details of a product. When you navigate to it, you will usually need to pass the product parameter to display:

```csharp
await Nav.Go<ACachedProductViewPage>( new { product = myProduct } );
```

On the target page then you will be using the product data to populate the UI. For example, you might have the following code:

```csharp
public override async Task OnInitializing()
{
    await base.OnInitializing();
    await InitializeComponents();
    
    LoadProductDetails();
}

void LoadProductDetails()
{
     var product = Nav.Param<Product>("product");
     ProductTitle.Text = product.Name;
     ...
}
```

But remember there is always only one instance of that page cached, **so if you navigate to the same page with another product as nav parameter, the new parameter will be ignored and the page will still show the old product's details.**

To solve that problem, you need to make sure that if a page is cached, it can also update itself upon being Shown again:

```csharp
public override async Task OnInitializing()
{
    await base.OnInitializing();
    await InitializeComponents();
    
    LoadProductDetails(); // We keep this line for a slightly better first-time loading experience.
    await WhenShown(() => LoadProductDetails());
}
```

#### Cleaning up the cache

In case you need to remove all pages from the cache, you need to call the following method:

```csharp
Nav.DisposeCache();
```

For example, if your app has a Logout functionality, it's a good idea to clear the cache to prevent unintended security issues.