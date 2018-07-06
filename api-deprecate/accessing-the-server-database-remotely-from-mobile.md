
### ACCESSING THE SERVER "DATABASE" REMOTELY FROM MOBILE

The Api class in mobile app inherits from Zebble.Framework.BaseApi. It's used as a gateway to access all server side APIs. You can use it in a similar way as the Database class. For example you can use:

```csharp
Api.Get<Customer>(myId)
```
```csharp
Api.GetList<Customer>()
```
```csharp
Api.GetList<Customer>(c => c.Category.Name == "MOP")
```
```csharp
Api.Save(myCustomer)
```
```csharp
Api.Delete(myCustomer)
```

These methods in turn invoke the server API and take care of security, serialization, mapping, etc.

#### How does it work?

The following process takes place when you make the above call from the mobile app:

A HTTP request will be sent to **.../api/v1/db/Customer**<br>
The server API will receive the call. It will then run the security checks and breaks if the call is not permitted.<br>
It will then check the explicitly permitted types and try to find an equivalent type in the server application to "Customer". If found, the database query will be executed.<br>
 
The data will be then serialized into JSON.
 
The JSON response will be sent to the mobile app, which will then deserialize it into a list of Customer type and return it to the caller.