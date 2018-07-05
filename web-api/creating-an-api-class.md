
### CREATING AN API CLASS

#### Step 0 - BaseApiController (only once)

You can create Custom APIs using the standard WebApi Controllers. But it's recommended that you add a base class for all your APIs to enable code reuse for common things such as security.

In your Website project, Add a folder named API and add the following class:

```csharp
using Domain;
using MSharp.Framework.Api;

namespace Controllers.API
{
    public class BaseApiController : ApiController
    {
        protected new User User => base.User as User;
    }
}
```

You can come back to this and add more code that you want to reuse in other application controllers later on.

#### Step 1 - Add a custom controller

Each API class should be for dealing with one particular aspect of the system (e.g. Authentication, or Product management, or Xyz).

Add a controller class for the intended feature or category that you need to implement, e.g. ProductApiController.
Inherit from BaseApiController.

```csharp
namespace Controllers.API
{
     [Authorize, RoutePrefix("api/v1/products")]
     public class ProductController: BaseApiController
     {
           [HttpGet, Route("")]
           public object GetAll()
           {
                 var products = Database.GetList<Product>(p => p.Owner == User);
                 var result = products.Select(item => new
                 {
                        Id = item.ID,
                        Name = item.Name,
                        ImageUrl = item.Image?.Url(),
                        Category = item.Category
                });

                return Ok(result);
            }
}
```

**Notes:**

- The  [**RoutePrefix**("api/v1/API-AREA")] attribute on the class is required. If the API you're creating is for a new version, then change v1 to v2, etc. This allows the previously installed Apps to continue using api/v1, but the new ones to directly request this. You don't need to create a new version if your changes are not going to break the previously installed Apps.
- For each actual API, you should add a method.
  - Specify **[HttpGet]** if the API method does not change anything on the server (such as Get, Find, Search, GetList, etc).
  - Specify **[HttpPost]** if the API does change data on the server (such as Add, Update, PlaceOrder, etc)
- Add a [**Route**("address")] attribute.
  - The full URL of the API will be a combination of the class-level **RoutePrefix** plus the method-level Route.
  - The above example can be queried using the URL of **.../api/v1/products** (as I've left the Route address empty).
- A **HttpGet** method is always expected to return some data using the **Ok()** method. By default, it will return Json. But it can also return XML if the client has asked for it (using Accept request header). In any case, the **Ok()** method will take care of the serialization to the correct format.
  - To return a single object back, return one anonymous object.
  - To return a set of objects, return an IEnumerable of anonymous objects similar to the above example.
  - For images, do not return the full binary data. Return just the URL instead.

#### Step 3: Additional APIs related to the same category

You can add additional API methods to the same controller as long as they belong to the same concept or sub-system in your application.

```csharp
[HttpPost, Route("add")]
public object Add(Product product)
{
       if (User == null)
             return Unauthorized("Unauthorised access");       

       if (someValidationCondition)
             return BadRequest("My error message");

        // TODO: After validation, do what needs to be done (e.g. save in database, etc).

        return Ok();
}
```

Notes:

- In the above example, the client (mobile app) can call the API with the url of **.../api/v1/products/add**
- Always validate the input as well as the caller's permissions before running the logic. See the example above. If the request is not valid, then return with an appropriate response method. Return
  - **Unauthorized(...)** for security problems
  - **NotFound(...)** for when the specified parameters are not found (e.g. a requested object ID that doesn't exist in database)
  - **BadRequest(...)** for anything else.
  - 
If you don't need to return any data back to the client, return **Ok()**