
### INTRODUCTION: "RELEVANT" DATA

In almost every mobile application you need to have a data synchronisation between the app and the server.
In M#, Zebble mobile projects, you typically have the following situation:

- There is an offline Sqlite database in the App.
- There is an MVC application (with a SQL Server database, and some APIs) sitting on a server, accessible via a URL.
- The SQL Server database on the server is the primary repository of the overall data.
- Some of that data is for internal administration only and never exposed to the mobile apps. Such data can be ignored for this purpose.
- Some other data is **"relevant"** to the Apps. E.g. the app will use, create or update that data.
- For the latter we need to have some kind of communication or synchronisation between the App and the server database.