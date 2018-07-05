
### PLAYING REMOTE VIDEOS IN IOS

To make your videos playable on iOS devices, you need to implement support for byte-range (or partial) requests. These type of requests allow downloading not the whole content, but partially, chunk by chunk (typical streaming). And this is the only way how iOS devices get and play videos on the page.

For this purpose change your DownloadFile action on SharedActionsController to something like this:

```csharp
[Route("file/download")]
[EditorBrowsable(EditorBrowsableState.Never)]
public ActionResult DownloadFile()
{
    var path = Request.Url.Query.TrimStart('?');
    var accessor = new FileAccessor(path, User);
    if (!accessor.IsAllowed()) return new HttpUnauthorizedResult(accessor.SecurityErrors);
    if (accessor.Document.IsMedia()) return new RangeFileContentResult(accessor.Document);
    else return File(accessor.Document);
}
```