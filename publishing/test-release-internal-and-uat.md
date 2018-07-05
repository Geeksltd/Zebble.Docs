
### TEST RELEASE (INTERNAL AND UAT)

During the development and testing phases of a mobile app project, you may need to install the app on the internal testing devices, or even the client's phone for review and feedback. Also, most apps will have a web api that needs to be hosted on a server.

#### Versioning Problem: Mobile App vs Web API

During the development process, the app code and the Web API code often need to be updated together, so they match. For example if you change the ROUTE of a Web API method, or its signature (parameters, etc) if the appropriate changes are not applied on the app as well, it can break.

Consider the following scenario:

- You have your App version v1 with the Web API version v1 ready for testing.
- You deploy the web api on a server on the URL https://myapp.uat.co.
- You configure your mobile app's config xml file to use that URL.
- You deploy the app on the internal testing device or the client's device and everything seems working fine.

Then after that:

- You continue development and change the application and create v2.
- You deploy the v2 version of the Web API on the server on the same URL: https://myapp.uat.co
- You deploy the v2 of the app on internal testing devices and everything works fine.
 
**Wait a second!**

On the testers' or the client's device, the app is still v1 and it's pointing to the same web api URL, which is now hosting v2. As a result, the app can break and you will have to physically gain access to the device again to install v2, which would be very annoying due to the wasted time, confusion and possibly travelling costs.

#### Versioning Solution

To address this problem you need to ensure that whenever you install an app for a tester or the client, the web api will not change after that, for as long as you need that version of the installed app to work.