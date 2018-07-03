
### LAZYLOADER

The LazyLoader component in Zebble allows you to improve the user experience by loading time-consuming contents after navigation to a page starts.

Imagine if you have a page to show a list of products. That page will use an API to download the data of products and it will then use it as the data source of a list module.

If you invoke the Web API at the Initializing stage of the page, when the user taps a link to go to that page, she has to wait until it's finished before the navigation animation starts. That is a waste of the user's time and also leads to poor user experience.

Instead, you should run the following in parallel:

- Processes on the target page such as downloading the data from a Web API and building the list module
- Page Transition animation to that page.

You can achieve that by using the LazyLoader component in Zebble.

```xml
<LazyLoader>
      <.... />
</LazyLoader>
```