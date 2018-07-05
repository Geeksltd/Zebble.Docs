
### INSTALLATION

#### M# MVC application (Server)
In the server application:

- Add a NuGet package to **MSharp.Framework.Api** and **JWT** (1.3.4) to website
- In the Website project, add a folder named API.
- In web.config, add an app setting for **"JWT.Token.Secret"** with a random text of 20 characters.

Add the following to the very first line of Application_Start:

```csharp
GlobalConfiguration.Configure(config => config.MapHttpAttributeRoutes());
```
 

#### Mobile App (Client)

Ensure that in Config.xml you specify the following:

```xml
<Api.Base.Url>https://123.123.123.123:7890</Api.Base.Url>
```

**NOTES:**

Specify your computer's IP address, and the port number that your Web App responds to - as set up in IIS.
Use your computer's network IP address instead of 127.0.0.1. Otherwise, you won't be able to test it from an emulator or a device (where "127.0.0.1" doesn't mean your development Windows machine!). 127.0.0.1 will only work on your local UWP app version.
In Windows Firewall, add an in-bound rule to open the port number you use to enable iOS and Android to connect to your Web Api.