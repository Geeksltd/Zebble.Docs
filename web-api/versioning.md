
### VERSIONING

When you release a mobile app, it will be using the API url of the server as configured, for example:

```
/api/v1/my-service
```

If in a new release of an application you wish to change the implementation in a way that breaks the old schema it will cause the existing installations of your application to crash.

To fix this problem you should always ensure backward compatibility of the Apis.

If you need to introduce a breaking change to an API you should create a new controller so the URL of the Api becomes:

```
/api/v2/my-service
```

**Notes**

After a while, your application may have a mix of APIs with different versions. That's OK. You don't have to recreate the older APIs which are still relevant and bring them to the new version.

#### Migration

When you make a change in the Apis and yet have to maintain multiple versions of it, instead of copying and pasting lots of code, a common best-practice is to keep a single implementation of the API which is always the latest version, but then update the implementation of the old API to adapt the input or output so it's compatible with the latest version. 