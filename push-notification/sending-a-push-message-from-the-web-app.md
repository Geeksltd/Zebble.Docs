
### SENDING A PUSH MESSAGE FROM THE WEB APP

Add a Nuget Reference to:

- MSharp.Framework.Api
- PushSharp

#### UserDevice entity

Create an entity in your project named UserDevice. It should have the following properties. For each installation a record will be inserted into this table.

- **InstallationToken** (string, unique, mandatory) -> This is a uniquely generated value that the mobile app will send to register the installation on a device for a particular user.
- **InstallationTime** (DateTime, mandatory) -> This is saved at the same time as the above property.
- **User** (association, optional) -> The user entity in your application
- **DeviceType** (string, mandatory) -> Values should be exactly one of  iOS, Android, or Windows .
- **PushNotificationToken** (string, optional) -> The value for this will be sent by the devices and saved via the API when they sign up for push notification.
- **LastLogOff** (DateTime, optional) -> Set via API as soon as the user logs off. When the user logs back in, this gets removed.
 

**Note:** It should implement: MSharp.Framework.Api.PushNotification.IUserDevice

#### Authentication API 

```csharp
[HttpPost, Route("push-notification/register")]
public IHttpActionResult RegisterPushNotification(User user, string installationToken, string pushNotificationToken, string deviceType)
{
    var device = UserDevice.FindByInstallationToken(installationToken)?.Clone() ?? new UserDevice();

    device.User = user;
    device.InstallationToken = installationToken;
    device.PushNotificationToken = pushNotificationToken;
    device.DeviceType = deviceType;
    device.InstallationTime = LocalTime.Now;
    device.LastLogOff = null;
    Database.Save(device);

    return Ok(device.PushNotificationToken);
}

// Unregisters user's device
[HttpPost, Route("push-notification/unregister")]
public IHttpActionResult UnregisterPushNotification(string installationToken)
{
    var device = UserDevice.FindByInstallationToken(installationToken);
    if (device != null) Database.Update(device, d => d.PushNotificationToken = null);

    return Ok();
}
```

#### Logging Off

When the user logs off from the App, it should call an API and send the installation token with it to then update the user device record.

```csharp
[HttpPost, Route("logout/{installationToken}")]
public IHttpActionResult Logout(string installationToken)
{
      UserDevice.FindByInstallationToken(installationToken)?.SetDeviceAsOffline();
      return Ok();
}
```

--------In the UserDevice logic file ------------

```csharp
public void SetDeviceAsOffline() => Database.Update(this, d => d.LastLogOff = LocalTime.Now);
```