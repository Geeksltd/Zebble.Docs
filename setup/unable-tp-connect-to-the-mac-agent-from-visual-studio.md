
### UNABLE TP CONNECT TO THE MAC AGENT FROM VISUAL STUDIO

If you are not able to connect to Mac agent from VS and you are getting this error in logs:

- "Unable to connect to Address='192.168.1.2:22' with User='macuser'"

- On your machine go to the following directory:

```
C:\Users\{YOUR.USERNAME}\AppData\Local\Xamarin\MonoTouch
```

- Delete id_rsa and id_rsa.pub files and try to connect again.