
### UNIQUELY IDENTIFYING INSTALLATIONS (TOKEN)

When an app is installed for the first time on a device, a file named **Installation.Token** will be generated automatically in the resources folder. Its content will be a **generated Guid**.

To access the token at runtime, you can call **UIRuntime.GetInstallationToken()**.

It is a good idea to send this token, along with the **Device.Platform** value to the server when logging in or registering a user.

As each user can potentially access your platorm from multiple devices, on the server app create a new entity type named **UserDevice** with the properties of:

- **User** (association)
- **DeviceType** (string)
- **InstallationToken** (string)