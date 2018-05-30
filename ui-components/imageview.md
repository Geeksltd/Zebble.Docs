[basicusage]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Basic.png "Zebble-ImageView"
[Stretch-Fill]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Fill.PNG "Zebble-ImageView-Fill"
[Stretch-Fit]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Fit.PNG "Zebble-ImageView-Fit"
[Stretch-AspectFill]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/AspectFill.PNG "Zebble-ImageView-AspectFill"
[Stretch-Default]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/TopLeft.PNG "Zebble-ImageView-Default"
[Default-TopLeft]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/TopLeft.PNG "Zebble-ImageView-Default-TopLeft"    
[Default-TopRight]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/TopRight.PNG "Zebble-ImageView-Default-TopRight"    
[Default-TopMiddle]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/TopMiddle.PNG "Zebble-ImageView-Default-TopMiddle"
[Default-Left]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Left.PNG "Zebble-ImageView-Default-Left"  
[Default-Right]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Right.PNG "Zebble-ImageView-Default-Right"       
[Default-Middle]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/Middle.PNG "Zebble-ImageView-Default-Middle"
[Default-BottomLeft]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/BottomLeft.PNG "Zebble-ImageView-Default-BottomLeft"
[Default-BottomRight]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/BottomRight.PNG "Zebble-ImageView-Default-BottomRight"
[Default-BottomMiddle]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/BottomMiddle.PNG "Zebble-ImageView-Default-BottomMiddle"
[Default-None]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/None.PNG "Zebble-ImageView-Default-None"
[Default-Justify]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/imageview/None.PNG "Zebble-ImageView-Default-Justify"

#### ImageView
ImageView allows you to display an image. It can display an image from an internet URL, or from a local image file under **App.UI\Resources** folder.

##### Basic usage
```xml
<!-- Displaying an image saved under C:\....\App.UI\Resources\Images\something.png -->
<ImageView Id="MyImage" Path="Images/Something.png" />
<!-- From a live URL -->
<ImageView Id="MyImage" Path="http://mywebsite.com/images/something.png" />
<!-- From a binary stream, or byte[] -->
<ImageView Id="MyImage" ImageData="@GetSomeByteArray()" />
```
![basicusage]

##### Stretch
You can set the stretch property to specify how the image should be rendered. 
```xml
<ImageView ... Stretch="Fill" />
```
The options are:

**Fill:** Stretches the image to completely and exactly fill the display area. This may result in the image being distorted.

![Stretch-Fill]

**AspectFill:** Clips the image so that it fills the display area while preserving the aspect (ie. no distortion). This is generally preferred to Fill.
 
![Stretch-AspectFill]

**Fit:** Letterboxes the image (if required) so that the entire image fits into the display area. This may result in blank spaces around the image if the aspect-ratio of the image differs from that of the display area.

![Stretch-Fit]

**Default:** Align the image to an arbitary position by setting the `Alignment` property.

![Stretch-Fill]

<br>

Also in CSS you can set it using background-size.
```css
.my-selector
{
     background-size: contain; /* ----> Equivalent to Fit*/
     background-size: cover; /* ----> Equivalent to Fill*/
     background-size: initial; /* ----> Equivalent to Default*/
     background-size: auto; /* ----> Equivalent to AspectFill*/
}
```
##### Image Alignment
When the stretch is Fit or None, then you can specify where in the image view box the actual image should be aligned.
```xml
<ImageView ... Stretch="Fit" Alignment="TopLeft"/>
```
###### Your options are: 
| Alignment     | Stretch         | Result  |
| :------------ | :-------------- | :------ |
| TopLeft       |      Default    | ![Default-TopLeft] |
| TopRight      |      Default    | ![Default-TopRight] |
| TopMiddle     |      Default    | ![Default-TopMiddle] |
| Left          |      Default    | ![Default-Left] |
| Right         |      Default    | ![Default-Right] |
| Middle        |      Default    | ![Default-Middle] |
| BottomLeft    |      Default    | ![Default-BottomLeft] |
| BottomRight   |      Default    | ![Default-BottomRight] |
| BottomMiddle  |      Default    | ![Default-BottomMiddle] |
| None          |      Default    | ![Default-None] |
| Justify       |      Default    | ![Default-Justify] |

You can also set it via CSS using the background-position attribute:
```css
.my-image {  background-position: center; }
```
##### Image-loading optimization
Loading and displaying images (even from the local disk) is time-consuming and can slow down the page render time.

Zebble offers the following to solve this problem:

- All images in the **App.UI\Resoruces\Images\Icons** folder are cached in memory once loaded.
- All other images (even locally saved) will be loaded after the page is displayed. 

To get the best result, you should include all decorative app images related to the design of the app inside the Icons folder. Alternatively, you can register additional folders to be treated like the Icons folder for immediate loading and caching in memory using the following:
```csharp
// Add this to your StartUp.cs
ImageService.MemoryCacheFolder("images/MyFolder");
ImageService.MemoryCacheFolder("images/AnotherFolder");
```
Alternatively you can add a specific image file or URL to be cached:
```csharp
ImageService.MemoryCacheFile("images/one-specific-file.png");
ImageService.MemoryCacheFile("https://some-url/file.png");
```
##### Background image caching

Instead of using an ImageView tag you can of course use the backgroundImagePath  property of any other view type. In that scenario if you need to cache the background image, then you can use the following attribute:
```xml
<AnyView BackgroundImagePath="https://some-image/path.png" z-cache-background-image="true" />
```
##### Remote Images (URL)
When it's a URL, then:

Instead of waiting for the actual image to be downloaded, the rendering continues with a default image named **App.UI\Resources\Images\loading.png** which is a placeholder image.
In the background, the remote image will be downloaded and saved locally as **A[device cash folder]\_cached\[URL-HASH].image.**
Then after the page is rendered and the image downloading is completed, it will automatically swap the image source to the downloaded cached image.
All subsequent requests to the same URL will be served from the local cache.

##### Lazy Loading

Since memory management is fierce on mobile devices (especially iOS devices) all the lazy loading you can implement will give your app a better memory footprint. You can use IsLazyLoading property to increase the performance of image loading.

It is recemonded that set it to True always.
```xml
<ImageView IsLazyLoaded ="true"/>
```
```csharp
await Body.Add(new ImageView { IsLazyLoaded = true });
```
##### Path

You can set the image file with Path property.
```xml
<ImageView  Path="Images/Logo.png"/>
```

### Events
| Event             | Type                                          | Android | iOS | Windows |
| :-----------      | :-----------                                  | :------ | :-- | :------ |
| on-Flashed            | AsyncEvent    | x       | x   | x       |
| on-Initializing            | AsyncEvent    | x       | x   | x       |
| on-LongPressed            | AsyncEvent    | x       | x   | x       |
| on-PanFinished            | AsyncEvent    | x       | x   | x       |
| on-Panning            | AsyncEvent   | x       | x   | x       |
| on-PreRendered            | AsyncEvent    | x       | x   | x       |
| on-Swiped            | AsyncEvent   | x       | x   | x       |
| on-Tapped            | AsyncEvent    | x       | x   | x       |
