
### OPTIONS FOR IOS APP DISTRIBUTION

#### 1) The Public App Store

**Pro’s**

Apple provides the distribution service – The App Store. It is highly available and well understood by users. <br>
The App Store may promote your company on a highly visible marketplace.<br>
Requiring a small price (such as 99 cents) will discourage casual installations which adds an element of protection to your app.<br>

**Con’s**

It requires an iOS Developer license for $99 per year.<br>
The App Store approval process is required for initial app deployment and app updates. You may be required to make changes to the app. The approval process can take a few days or a few weeks.<br>
The App Store provides information about your app to competitors including a description of the app’s features, screenshots and an indication when the app is updated.<br>
If you charge a price for the app, 30% of the revenue goes to Apple.<br>
 

#### 2) iOS Developer Enterprise Program

The iOS Enterprise Distribution program allows a company to distribute their own “in-house” apps directly. It is intended for employees of the licensee company only and that licensee must be a company or organization with a DUNS number. 

**According to apple:**

“Internal Use Applications developed under this Agreement may be deployed on Deployment Devices in two ways: (1) deployment for internal use by Employees, and (2) deployment for use by Customers either on Your physical premises or under the direct supervision and physical control of Your Employees in other locations, subject to Apple’s right to review and approve such deployment as set forth herein.”

**Pro’s**

The App Store approval process is not required.<br>
The general public cannot see a listing for your app, purchase or install it. It is not on the App Store.

**Con’s**

The Enterprise program is intended for employees and contractors of the licensee only.
The licensee is responsible for distributing and updating the app. This can be done manually by email, making the app available on an Intranet site, through a Mobile Device Management System (MDM), etc.
The cost is $299 per year for the Enterprise Developer Account compared to $99 per year for the iOS Developer Account.
Each device can have apps installed from only one iOS Enterprise License at a time.
 

#### 3) Custom B2B Apps Program

Apple has programs for volume purchasing and custom B2B apps. These programs operate from the online Business Store. The Volume Purchasing Program allows businesses to buy apps from the public App Store in bulk. Custom B2B Apps extend the Volume Purchase Program for custom B2B apps built by third-party developers. The third-party developer determines which Volume Purchase customer(s) can purchase a given app. Such apps are not available on the public App Store but only through the Business Store.

**Pro’s**

More convenient for larger distributions. Each individual installation does not require a user to make a purchase through the public app store and expense the cost. Instead, users are given a coupon that they can use to install the app.<br>
Apple provides the distribution service – the Business Store. This provides some features of an MDM.<br>
The general public cannot see the listing, purchase or install the app.<br>

**Con’s**

Requires App Store approval process for initial app and updates.<br>
If you charge a price for the app, 30% of the revenue goes to Apple.<br>
B2B apps are only available to businesses enrolled in the Volume Purchase Program. The Volume Purchase Program is limited to 10 countries as of May 2013: Australia, Canada, France, Germany, Italy, Japan, New Zealand, Spain, United Kingdom, and United States

**Note:** An iOS Developer License is required to use the Custom B2B Apps Program. Limiting an app to the B2B App Store is an option when submitting to the Public App Store.

 

#### 4) Ad Hoc Distribution (intended for Testing)

Ad Hoc Distribution allows you to distribute apps to up to 100 iOS devices for testing. You must register these devices manually by their ID. Devices can be removed/replaced once each membership year). Ad Hoc Distribution is a feature of both the iOS Developer Program and the iOS Developer Enterprise Program. This may be all that is needed for a prototype or trade show.

**Pro’s**

The App Store approval process is not required.<br>
The general public cannot see the listing, purchase or install the app.<br>
Over-the-air installation from a hyperlink (hosted on your web server or on an iOS Beta Testing Service *mentioned next) or by emailing to a computer with iTunes installed (and then installing to the device).<br>

**Con’s**

Limited to 100 devices (devices can be removed/replaced once each membership year).<br>
The UDID (Unique Device IDentifier ) of each device must be associated with your provisioning profile. This is a manual process.<br>
Your team must manage deployments and updates.<br>
The related developer provisioning profile expires in one year. This means that the app will run on a given device for a maximum of one year. When the Developer Provisioning profile expires the app will need to be rebuilt with a new provisioning profile.<br>

**How?** [This article](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/app_distribution/ipa_support/) covers how to create an IPA file that can be used to deploy an application using Ad Hoc distribution, either for testing, or for In-House distribution of internal applications.

#### 5)  iOS Beta Testing Service: TestFlight

TestFlight is a free over-the-air platform used to distribute beta and internal iOS applications to team members. Developers can manage testing and receive feedback from their team with TestFlight’s Dashboard.

TestFlight makes use of your iOS Enterprise License or Developer License to create Enterprise and Ad Hoc provisioned apps.

**Pro’s**

The same Pro’s as #2 iOS Developer Enterprise Program or #4 Ad Hoc Distribution depending on which iOS license you use.<br>
Distribution and feedback is managed with a free, cloud based service.

**Con’s**

The same Con’s as #2 iOS Developer Enterprise Program or #4 Ad Hoc Distribution depending on which license you use minus the Con about managing deployments and updates.