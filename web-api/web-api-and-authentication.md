
### WEB API AND AUTHENTICATION

We use JTW authentication. This is how it works.

#### Initial Authentication

The user will logon in the mobile app (e.g. using a username and pass, or with social login)
The login API will generate and return a JWT Token which is an encrypted piece of data with {UserID , ExpiryDate}. Example:

```csharp     
[Route("login")]
public object Login(string email, string pin)
{
   if (email.IsEmpty() || pin.IsEmpty()) return BadRequest("Email and pin must be provided.");
   var user = Database.Find<Member>(m => m.Email == email && m.Pin == pin);
   if (user == null) return BadRequest("Email or pin is invalid.");
   return JwtAuthentication.CreateTicket(user);
}
```

The client app (mobile) will save the JWT token in a local file (recommended name: **SessionToken.txt**)

#### Subsequent API calls

- Then everytime an API method is called on the mobile app, the token will be sent via Header.
  - The header key will be **Authorization** and the value will be Bearer `<token>`
  - The value of `<token>` will come from calling `BaseApi.GetSessionToken()`.
  - The default implementation for GetSessionToken() is Device.IO.File(**"SessionToken.txt"**)?.ReadAllText()
  - If you want to change the default implementation, in your app StartUp.cs file you can write:

```
BaseApi.GetSessionToken = () => {your code};
```
The Api Controller will read the token from the header, decrypt it and set the current user of the HttpContext correctly.<br>
This takes place in the base controller class which is MSharp.Framework.Api.ApiController.<br>
In the API method implementation you can simply invoke this.User or HttpContext.Current.User in order to verify the user's permissions or to filter the returning data, etc.<br>