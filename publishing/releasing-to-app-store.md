
### RELEASING TO APP STORE

#### iOS App Store

https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/app_distribution/app-store-distribution/publishing_to_the_app_store/

- Create a new App ID (Also referred to as Bundle ID) here: https://developer.apple.com/account/ios/identifier/bundle 
Name it such as "My application"
Select an App ID Prefix
Bundle ID should be in the format e.g: com.my-domain.MyApplication  . This should be the same as your config.xml (key of Application.ID) and info.Plist (key of CFBundleIdentifier)
Select the services if necessary.
Create a Distribution Provisioning profile at https://developer.apple.com/account/ios/profile/production
Then download and install it on XCode on the Mac.
It should then be selected in Visual Studio for Release or AppStore build.
- Create a new App in https://itunesconnect.apple.com/WebObjects/iTunesConnect.woa/ra/ng/app
Select iOS checkbox
Name should be "My application".
BundleID should be the one you just created.
SKU should be: MyApplication
On the next page, select the **Category** and press Save
- Under Pricing and Availability, add a price and save
- Go to Prepare for submission page and upload 5 screenshots.
Install the app on an iPhone 6 Plus and take screenshots from the actual iphone.
Email the images to yourself (full quality) to then upload.
Their resolution must be 1242 x 2208 and with 72 DPI.
- If you're using iPhone 6, then use Paint.Net to resize the image to the above.
If you need to support iPad too, then repeat the above based on 2048 x 2732
Save and go back to Prepare for Submission page.
Write a full description of the app. Check Apple's guidelines for this.
Create a Distribution Provisioning profile at https://developer.apple.com/account/ios/profile/production
Install the generated certification

#### Android:

https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/publishing_an_application/part_1_-_preparing_an_application_for_release/