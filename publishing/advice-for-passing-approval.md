### ADVICE FOR PASSING APPROVAL

[Read the full Xamarin guide](https://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/part_6_-_testing_and_app_store_approvals/)

Test your app thoroughly before submitting it, focusing not just on making sure everything works but also that you handle common mobile error scenarios such as network problems and resource constraints like memory or storage space
Use both the simulator and physical devices to test
Use as many different devices as you can find, and enlist a team of beta-testers if you can - third-party services can help manage beta distribution and feedback.
Always provide user feedback when something is happening in the background, or the app will appear to have crashed and once again, get rejected.
Applications should degrade gracefully (and not crash) when a component is unavailable such as network, camera, microphone, GPS, gyroscope or other optional component.
Put as much effort into the application’s metadata as into development and testing. Applications DO get rejected for minor infringements in the metadata so it is worthwhile taking the time to get it right. 