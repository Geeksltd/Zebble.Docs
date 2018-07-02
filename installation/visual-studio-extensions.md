
### VISUAL STUDIO EXTENSIONS

#### SASS Compiler

SASS is the preferred format for writing styles in Zebble. SCSS files are compiled into CSS which is then compiled into C# by Zebble Builder.

- In Visual Studio extensions, install **"Web Compiler"** and then restart visual studio.
- A file named compilerconfig.json is added to your project folder. Right click and include it in the project.
- Right-click the compilerconfig.json file and press Web Compiler -> "Enable compile on build"
- In **Visual Studio > Tools > Options > Text Editor > SCSS > Advanced**
    - set **Automatic formatting** to **On**.
    - set **Brace positions** to **Compact**.

#### CSS Color Highlighter
The extension highlights any color in CSS file with that color. Supported color syntax: rgb(), rgba(), hsl(), hsla(), HEX and 147 web color names.

[Click to install](https://marketplace.visualstudio.com/items?itemName=Smoria.ColorhighlighterforCSS)