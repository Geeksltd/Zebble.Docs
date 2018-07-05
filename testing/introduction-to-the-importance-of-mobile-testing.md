[mobiletesting]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/testing/mobiletesting.jpeg

### INTRODUCTION TO THE IMPORTANCE OF MOBILE TESTING

#### The Importance of Mobile Testing
 
![mobiletesting]

It is a digital world, and all Generations have embraced the mobile revolution. It’s no surprise that millennials are leading the way. I saw a statistic recently that 85% of Millennials owns a smartphone. Next time you are waiting in line, take a look around.

 Statistics don’t lie.

Source: http://www.statista.com/chart/3760/mobile-etiquette/

The mobile revolution has only just begun. The importance of having a mobile testing strategy is critical to our app releases.

 
#### What makes a great mobile app?

There are multiple elements that can influence a great (or bad) mobile app. The team works so hard developing an app (from idea, planning, writing code, and testing), the last thing you want to hear is negative feedback instantly after releasing the app. As long as the focus is on simplicity, understanding your users (audience), and the performance of your app, you are heading in the right direction.

**Simplicity:** Keep the design simple. A common mistake with app developers is to overdesign. It is important to make sure your design is as simple as possible for everybody.

**Know Your Users:** They are many different types of users, therefore it’s important to think about how each category will approach it.

**Performance:** Mobile users expect and demand the same level of performance from their mobile apps as they get from their desktop computers. I recently read an article where 3 seconds or less is considered as fast and acceptable. How does your mobile app handle a load of multiple concurrent users? Does it maintain a response time of less than 1 second? The speed of loading the app or content within the app is critical. Most mobile users rarely give problematic app’s a second chance. First impressions are critical. Do you know the number one bug reported for mobile apps? It appears when rotating from portrait to landscape or vice versa, and causes the app to crash. Adding unit, functional user interactions, and load testing is a step in the right direction in building a robust app.

Functionality and shareability are other important guidelines to think about when developing a great mobile app.

#### Test your hearts out

The pressure to get mobile apps built, tested, and deployed has never been greater. It illustrates the importance of solid mobile testing strategies to ensure we build high-quality apps. Testing methods used previously for web applications do not meet the needs of current mobile applications. Now we are going to discuss testing strategy before releasing a mobile app. Test all the time, and do as much as you can at unit level.

**Unit tests** are the backbone of your mobile test strategy. They should happen early in the process of writing code. Doing this leads to better design. Writing unit tests helps you and others understand how your code works under different scenarios. (Whether the tests pass or fail, you’ll learn something about your code.) And it builds confidence in your code.

**Monkey testing** is a new technique in which the testing is performed on the system under test (SUT) randomly. Have you heard of [Chaos Monkey](https://github.com/Netflix/SimianArmy/wiki/Chaos-Monkey) by NetFlix? Failure happens. This tool prepares you for when bad things happen and allows you to isolate and resolve problems before they are released in the wild.

Try **Load (Performance) testing** using [BlazeMeter’s](https://blazemeter.com/) Mobile Recorder to achieve better load performance. It works by simulating mobile networks, setting thresholds, and testing user load by using as many concurrent users as you want.

Try **Functional User Interaction tests** using [Appium](http://appium.io/) to perform mobile gestures (press, long press, tap, drag and drop, swipe, rotate, and zoom) by using the [TouchAction](http://touchaction/) and [MultiTouchAction](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/touch-actions.md#multitouch) classes.

**Visual tests** are designed to catch unintended visual bugs when updating UI components. There is no way to know when an updated visual component breaks if you’re only running functional automated tests.