
### SUBMITTING TO APP STORE

- Go to the iOS project **Properties > iOS Build > General** and
Set Linker behavior to **Link SDK assemblies only**.
- **Check** the **Optimize PNG images files for iOS**.
- **Uncheck** the **Enable Debugging** option.
- Go to the iOS project **Properties > iOS Build > Advanced** and 
set **Supported architectures** to **ARMv7 + ARM64**.
- **Check** use **LLVM** optimizing compiler (Do not check subitems of LLVM)
- Go to the iOS project **Properties > iOS IPA Options** and
check the Build ad-hoc/enterprise package
- In package name textbox enter your desired package name
Remember **not** to check Include Artwork in IPA  
- Go to the iOS project **Properties > iOS Application** and set your identifier , icons and splash screens.
- Go to the iOS project **Properties > iOS Application** and set your App version and build version to something higher.
- Go to the iOS project **Properties > iOS Bundle Signing** and choose the provisioning profile that you created your identifier for it. (Note that this profile should be a Distribution profile).
- Go to the iOS project ***Properties** and set the **Configuration** type to **AppStore**. 
- Set the Visual Studio Solution **Configuration** type to **AppStore**. 
- Right click on your iOS project and press Deploy.

Your deployed file will be available shortly after that in following address: 
```
\M# Project Address\Run\iOS\bin\iPhone\AppStore\
```
Go to a Mac with XCode installed and Use Application Loader to upload your IPA file to AppStore.