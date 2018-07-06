
### OFFLINE PROGRAMMING MODEL

Many mobile apps stop functioning if Internet access is lost.

Our aim is to support offline functionality by **separating app functionality from server data sync**.

That is a great advantage and makes the apps extremely powerful.

To achieve this you should adopt the following thinking model:

- All modules (lists, forms, views, etc) will be defined in M# based on simply using a local database (without thinking about the API).
- All queries, deletes, saves, etc will take place on the local DB.
- A separate asynchronous worker will sync the data between the server and the local DB.

#### Exceptional scenario

There are some cases where a user action must not be performed if there is no Internet Connectivity available. Those are determined by each project's client requirements, security and common sense. For example if a server side validation is needed, or real-time requirements make offline use inappropriate. In those cases you should explicitly call the Apis from the UI and if they failed, then inform the user as validation messages.

There are other scenarios when the data shown to the user is the result of a **search on a big data set** on the server. In those cases we can't store the data locally as it doesn't make sense, and so an offline functionality is meaningless.

#### M# setting: IsUploadable 

Any entity type that is saved in the App and then synced (uploaded) to the server must set this property to true. That will use the ISyncTask framework (see below) to track changes and upload them to the server API.