[intro-1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/intro-1.png
[intro-2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/web-api/intro-2.png

### INTRODUCTION



Most applications need to connect to a server to download or upload data. The server application is often an ASP.NET web application with:

A SQL Server database as the primary repository of the overall data
Web-based UI for admin features
Web API to provide services to the mobile app.
 
![intro-1] 


#### Calling an API from Zebble apps

You can use the HttpClient class in your Zebble app to access the Web APIs with any server-side API architecture that you want to implement.

However, Zebble also comes with a layer on top of the raw HTTP tools of .NET to simplify things such as:

- Simplified addressing
- Security
- Versioning
- Exception handling
- Caching and offline support

This tutorial will guide you to create and consume Web APIs based on the M# MVC architecture.

#### Server database (SQL Server) v.s. App database (SqlLite)
 

Sometimes the data is meant to be solely for used within the mobile app and there may not even be a web-based interface or admin screen to see or change the data, and so for all intents and purposes some of the data may be originated and used only within the mobile App. In such cases, you might be tempted to keep the data only locally on the mobile app and avoid bringing the server (DB) into the picture.

![intro-2]

However, as a best-practice, you should always **use the server database as the ultimate home of all data**. The reason for that is that mobile database is unreliable. People may lose their phone and get a replacement, or uninstall and reinstall an app. Or they may upgrade their phone or move to another operating system. In any case, the local database on the app can easily vanish. In those cases, the users may expect to simply download the app again, log in and see their data in there. That's why you should always use a server-side database, and use APIs to make everything work.

Of course, the mobile database (SqlLite) also has its place, but mainly for temporary storage of data, or local caching for performance. 