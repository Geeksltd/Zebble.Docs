
### INTRODUCTION TO PUSH NOTIFICATIONS

Push Notification (PN) service is used to allow a server app to push notifications to mobile app installations. The server app will dispatch notifications to the mobile device indirectly, by sending it to a PN service:

- **Apple**: APNs (Apple Push Notification Service)
- **Google**: GCM (Google Cloud Messaging)
- **Windows**: WNS (Windows Notification Service)


To use this component, install the [Zebble.PushNotification](https://www.nuget.org/packages/Zebble.Plugin.PushNotification/) nuget package. 
It's open source and available on [GitHub](https://github.com/Geeksltd/Zebble.PushNotification). Also we welcome any contributions to enhace it.

#### How does it work?

The Zebble mobile app registers for push notifications with the PN service.
PNs sends a unique token back to the app, which is the unique id of that installation.
The app will then register the token with the server app (via its API).
The server app will store this token as an App Installation Record in the database.
Normally the installation token is also associated to a USER record in cases where the mobile app user is registered.
Then later on, the server app can deliver notifications to each token (i.e. mobile app installation) via the PNs.

**Notes**

The message/payload (including json data) should not be more than  256 bytes for Apple,  2KB for Android, and  5KB for Windows.
Within the above limit, you can send and command readable by the mobile app.
 

#### Implementation in the App

The Zebble project template contains a file named **App.UI\PushNotificationListener.cs**. All you need to do is fill in the blanks. It's fairly self explanatory.