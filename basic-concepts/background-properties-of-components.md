[background1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/background-properties-of-components/backgroundImage.png "Zebble-Background"
[background2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/background-properties-of-components/backgroundImage2.png "Zebble-Background"

### BACKGROUND PROPERTIES OF COMPONENTS

BackGround of each object is one of the main property which can give good effects to it.

The BackGround category is divided into **Image** and **Color** subcategories.

#### BackGround Image

You can determine an image among JPG, PNG, GIF, Icon to this property.

**MarkUp:**

```xml
<...   BackgroundImageAlignment="Middle" Style.Border="1" BackgroundImagePath="Images/image.png"/>
```

![background1]

You can use **BackgroundImagePath** for setting the path of an image file to any object. Also, if you want to align the position of image, you should set **BackgroundImageAlignment**. Meanwhile, by using **BackgroundImageStretch**, You can set the **BackgroundImageStretch** property to specify how the background image should be rendered:

**Fill:** Stretches the image to completely and exactly fill the display area. This may result in the image being distorted.
**AspectFill:** Clips the image so that it fills the display area while preserving the aspect (ie. no distortion). This is generally preferred to Fill.
**Fit (default):** Letterboxes the image (if required) so that the entire image fits into the display area. This may result in blank spaces around the image if the aspect-ratio of the image differs from that of the display area.

```xml
<... BackgroundImageAlignment="Middle" Style.Border="1"  BackgroundImagePath="Images/image.png"/>
<... BackgroundImageAlignment="Middle" BackgroundImageStretch="Fill" Style.Border="1"  BackgroundImagePath="Images/image.png"/>
<... BackgroundImageAlignment="Middle" BackgroundImageStretch="OriginalRatio" Style.Border="1"  BackgroundImagePath="Images/image.png"/>
<...   BackgroundImageAlignment="Middle" BackgroundImageStretch="Fit" Style.Border="1"  BackgroundImagePath="Images/image.png"/>
<...   BackgroundImageAlignment="Middle" BackgroundImageStretch="AspectFill" Style.Border="1"  BackgroundImagePath="Images/image.png"/>
```

![background2]