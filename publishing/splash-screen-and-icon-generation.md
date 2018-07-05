
### SPLASH SCREEN AND ICON GENERATION

Different platforms need you to provide several different images for  Splash screen and app Icon based on different device sizes. In total there are close to 30 different versions needed across all platforms.

We believe that manually creating them will be very time consuming and painful. That's why  Zebble offers an automated solution to generate them all automatically from a single file for each (splash and icon) that you provide once.

#### How does it work?

You need to have a high-res image named **Splash.png** and one called **Icon.png** at the root of your **App.UI** folder. You can update them during the development process, but every time they are changed you should run **Zebble.exe** with no parameter.

It will then automatically resize and cut the source images to create all the splash screen and icon files needed by the target platforms. The aspect ratio will be maintained and the image will not be squeezed by this tool.

You can check the generated files under:

- Run\UWP\Assets
- Run\iOS\Resources
- Run\Android\Drawable

#### Source Splash.png specification

To ensure you will have an acceptable quality generated for all sizes, you must ensure that your master Splash.png file conforms to the following requirements:

- Minimum of 3000px by 3000px
- Use a maximum of 50% of the width and height in the **centre** for the main content such as your **logo**.
- The rest of the image should be general graphic patterns or solid colour, in a way that it doesn't look bad when cropped.

#### Source Icon.png specification

To ensure you will have an acceptable quality generated for all sizes, you must ensure that your master Icon.png file conforms to the following requirements:

- Minimum of 1000px by 1000px
- Use a maximum of 95% of the width and height in the **centre** for the main content such as your **logo**.
- The rest of the image should be general graphic patterns or solid colour, in a way that it doesn't look bad when cropped.