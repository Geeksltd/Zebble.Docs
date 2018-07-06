
### ZEBBLE.FRAMEWORK.ISYNCTASK

In M# data synchronisation takes place using a Queue of sync tasks.

The ISyncTask interface in M# is defined based on the following. In the mobile app project, you have a class named **SyncTask** which implements this.

```csharp
public interface ISyncTask : IEntity
{
        double Index { get; set; }
        string ItemType { get; set; }
        string ItemId { get; set; }
        string Action { get; set; }
        string Error { get; set; }
        DateTime? LastAttemptUtc { get; set; }
        int Attempts { get; set; }
        bool IsDone { get; set; }
}
```

When a record is saved or deleted in the app, if that record is meant to be uploaded (synced) with the server, then a SyncTask record will be created.

So effectively we will have a queue of tasks waiting to be executed when Internet connection is available.

When internet access is available, a call will be made to **SyncTaskService.RunAll()** which will:

- Go through all outstanding tasks
- Run each one - i.e. call Api.Save() or Api.Delete() to upload the changes to the server via API.
- If there is any error returned from the server then the error will be saved on the SyncTask record.