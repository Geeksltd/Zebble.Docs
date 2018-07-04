
### CSS REAL-TIME UPDATES

During app development, when it comes to programming the styles, you often need to experiment with different attributes to get things right. This involves many rounds of making changes and observing the impact visually until you get it right.

Zebble makes it extremely fast and easy to do this.

#### Real time CSS updates

When you run the UWP version of your app during development, if you then change any CSS file, the app page will refresh automatically to reflect the changes. This process takes about half a second. So you can keep changing your styles, and immediately see the results without having to close the application, recompile, etc.

#### Under the hood

As UWP apps in windows don't have access to the local machine (beyond isolated storage) you might be wondering how this can work.

When you run your application in development mode from Visual Studio, a console application is also started which runs under the user account which has local permission to the app folder. It watches the App.UI folder in your project and waits for any change in your CSS files.

This console application also registers a http listener on the url **http://localhost:19765/Zebble/Css**.

The running UWP app will keep asking this process, via http, if there have been any changes. If changes were detected, the console app will transfer the full set of CSS to the running app. The running app will then remove all existing registered CSS rules and replace them with the new set.

#### Limitations

Any of your CSS rules which have been defined as a C# expression such as the following, will not be updated using the above mechanism.

```css
.my-selector { ...; width: calc("...my C# expression..."); }
```

- Any existing CSS rules containing calculated properties will remain running.
- Any newly written calc rules (or modified ones) will be ignored.
  - For seeing the change in those, you should close the app, compile and restart.