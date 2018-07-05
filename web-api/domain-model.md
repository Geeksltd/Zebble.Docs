[ex1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/ex1.png
[ex2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/ex2.png
[ex3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/ex3.png
[ex4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/ex4.png

### DOMAIN MODEL

#### Client Server System
 

 Your API application on the server probably has an object oriented architecture which is owned Domain Model or Business Entity classes. The mobile application also will have its domain layer with business objects or classes that they are usually similar in terms of global concept  as those on server API.

![ex1]


 For example, there can be a product concept that is existing both world with similar properties such as name, description and etc. So you might be tempted to reaze the code of classes and somehow share between the two apps For example, the packaging it in to a shared dialogue. However, as a role, it is usually better to resist a temptation an stick to completely separate classes on the mobile app compare to be api app. This way you will end up with the cleaner and more maintainable design, but more importantly a faster and more optimized application is better off line support.

![ex2]

 
 For example, if there are a list of products which come from an api. When the user taps an item, we show further details about the product, including technical aspects review and etc. In terms of the server side database, an application like this will probably have a complex structure and hierarchy related classes such as product category, product review, pricing rules, discount,suppliers information and etc.

![ex3]
 

The mobile app however need very little data and to keep thing safe and efficient which should definitely keep the server side object model separate from mobile app.

**Example:**


 For example, if there are a list of products which come from an api. When the user taps an item, we show further details about the product, including technical aspects review and etc. In terms of the server side database, an application like this will probably have a complex structure and hierarchy related classes such as product category, product review, pricing rules, discount,suppliers information and etc.
 
![ex4]
 

The mobile app however need very little data and to keep thing safe and efficient which should definitely keep the server side object model separate from mobile app.

  In the mobile app to cater from both of these pages, you can have a product class with not only Name, Price, ImageURL which are used on the list page, but also all of the properties for the detail page.
  Let us to start with the list page:
  We need to retrieve the products data from the API.
  But what we should return?

**Solutions:**

  1. One option is return the full product data and everything. So when we click to see details, all of the data should be downloaded. This means that we are potentially fetching tens of reviews and long technical aspect for many products which users are not going to be interested in necessarily. It is not only slow, but also it wastes the user's internet.
  2. We can only return the product ID, name, price and image url in the API. Then, when the user clicks on each item to see the detail information of item, we can call another web api to get full product data. Once received, we will then render the details page. This is faster and efficiently.