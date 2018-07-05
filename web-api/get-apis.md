
### GET APIS

For each API function that **only returns some data** (as opposed to SAVE or DELETE) you should add a **GET** based API.

```csharp
[Authorize, RoutePrefix("api/v1/orders")]
public class OrderController: BaseApiController
{
           [HttpGet, Route("orders/history/{param1}/{param2}")]
           public IHttpActionResult OrderHistory(string param1, int param2, string param3 /* from querystring */)
           {
                // Security checks: 
                if (! (User is Customer)) return Unauthorized("User is not a customer!");

                if (!myCustomValidationCheck()) return BadRequest("Some error message");

               var orders = User.Orders.Where(o => o.Date > args.Since);
               var result = orders.Select( o =>
               {
                      MobileProperty1 = o.Something,
                      MobileProperty2 = o.SomethingElse,
                     ...
               });

                return Ok(result);
           }
}
```

**Notes:**

- The parameters can be either added as url route, or as query string. In the above example:
  - param1 and param2 are route parameters
  - param3 is from query string
- Instead of serializing server-side domain objects directly, return anonymous objects that exactly match just the mobile domain's object.
This can lead to smaller return size.
  - It can give you more flexibility for an optimised design.
  - It can prevent accidental security issues of exposing sensitive data in the Json.