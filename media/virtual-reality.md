
### VIRTUAL REALITY

The Zebble VirtualReality component allows you to display a photo sphere image (360 degrees).

As you rotate the device around, the image view will be automatically updated to reflect the correct field of view.

#### Normal screen display

```xml
<VirtualReality Id="VR" BackgroundImage.Path="VR/Sun.jpg" GlassesMode="@GlassesMode" />
```

#### VR Glasses Mode

If you have VR glasses on your phone, then the following setting will turn the display into stereo mode which shows one image for each eye.

```xml
<VirtualReality Id="VR" BackgroundImage.Path="VR/Sun.jpg" GlassesMode="true" />
```