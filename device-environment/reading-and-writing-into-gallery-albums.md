
### READING AND WRITING INTO GALLERY (ALBUMS)

#### Pick an image from albums

The following will show a dialog to the user to pick an image from the device's local album.

```csharp
var photo = await Device.Media.PickPhoto();
if (photo != null)
{ 
     //  photo is a FileInfo...  
}
```

You can also use a similar approach to pick a video file by calling Device.Media.PickVideo().

#### Save an image file to gallery

Sometimes your app will download an image from an API, or generate a new image via some kind of processing. In that case, you might want to save the image in the device's albums folder. It's super simple to achieve that in Zebble:

```csgarp
FileInfo myImageFile = ...;
await Device.Media.SaveToAlbum(myImageFile);
```

The same method allows you to save a video file to the gallery too.