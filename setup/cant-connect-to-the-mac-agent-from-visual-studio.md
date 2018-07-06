
### CAN'T CONNECT TO THE MAC AGENT FROM VISUAL STUDIO?

Occasionally you may not able to connect to a Mac agent from your VS. If that happened to you, here is a workaround:

- On your machine go to the following directory:

```
C:\Users\{YOUR.USERNAME}\AppData\Local\Xamarin\MonoTouch
```

- Delete id_rsa and id_rsa.pub files
- Try to connect again.