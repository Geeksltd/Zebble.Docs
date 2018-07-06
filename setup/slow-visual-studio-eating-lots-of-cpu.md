
### SLOW VISUAL STUDIO (EATING LOTS OF CPU)?

If your Visual Studio is constantly using a lot of CPU, try the following solutions:

#### Disable Diagnostic tools

- Open Visual Studio
- Turn off Diagnostic Tools via Tools -> Options -> Debugging -> General
  - -> Uncheck **"Enable Diagnostic Tools while debugging"**.
- Go to Tools > Extensions & Updates
  - Disable the **Developer Analytics** Tools addon
- Close all VS instances

#### Delete corrupted VS temp files

Go to your **C:\Projects** directory<br>
Search for **name:=".suo"** files and delete them.<br>
Search for **name:=".vs"** and delete them.<br>
 
#### Virus Scan

Make sure a Virus Scan software is not interfering:

Disable your Virus Scan software and see if it impacts Visual Studio speed.
Turn it on again.
 
#### Clear VS Component Cache

If the other solutions didn't solve your problem, then try this.

**Beware: It will delete all of your Extensions and you have to [install them again](https://training.geeksltd.co.uk/a/TD/ZX3)**.

- Close all VS instances
- Go to **%localappdata%\Microsoft\VisualStudio**
- Delete any folder whose name starts with "15.0"
- Open VS again. It will show the preparation. It will take a few minutes.