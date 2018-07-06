
### REMOTE DATABASE ACCESS

By default, access to all entity types is restricted. So if a client tries to access `Api.GetList<SomeType>()` they will receive an error.

You need to explicitly grant access to enable reading the data for each type (and each property within that type) to ensure that no data is accidentally made available without proper checks in place.

#### Allowing read (for Api.GetList<> & Api.Get<>)

For each data type that you want to expose via the API you should add an AllowRead command in the DataServerApiController's static constructor.

#### Examples:

```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => true); 
// Open to anyone on the internet!
```
```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => User.IsAuthenticated()); 
// Open to any logged-in user.
```
```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => User.IsInRole("CertainRole")); 
// Role-based security.
```
```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => User.SpecialLogic()); 
// Custom permission checks
```

#### Default criteria

Sometimes you need to always **filter the data** available via the API. To achieve that you can use the following parameter:

```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => ..., appendCriteria: x => x.IsPublished);
```

Also note that any criteria requested by the client will be added to your criteria. So if they request: `Api.GetList<MyType>(x=> x.Date > someDate)` then the effective query that will run will be:  `Api.GetList<MyType>(x=> x.Date > someDate && x.IsPublished)`

#### PostQueryFilter

In the case of Default Criteria, sometimes your filtering logic cannot be represented as a database criteria. Instead, you need to define that as a C# boolean expression that is applied on the data coming from the database, before it's returned to the API caller. In that case you can use the postQueryFilter parameter.

**Examples:**

```csharp
Permission.AllowRead<MyType>(authorizeWhen: () => true, postQueryFilter: item => SomeCSharpLogic(item) );
```

Of course you can mix this parameter with **defaultCriteria** if you want to apply some of the filtering logic at the DB level and some at the application level.