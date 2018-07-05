
### REGISTRATION PROCESS (APP)

The app will contact the Apple or Google push notification server.
The APNS (or Google's service) will generate a unique token and return to the app.
The app will create an instance of PushNotificationListener class and call **OnRegistered(token, deviceType)**
Your implementation of OnRegistered() should register the token with the server API. For example:

```csharp
await Api.Post("v1/authentication/register-push-notification", new {Token=token, DeviceType = deviceType } );
```

*Your API should then save the deviceType and Token value on the user record.
Now the server application knows the device type (iOS, Android, etc) as well as the token for each user and can send them a push notification.*