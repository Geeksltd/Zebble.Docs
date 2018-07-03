
### USING BOLD AND LIGHT FONTS IN ZEBBLE

In Zebble when you want to use Bold, Light or UltraLight versions of a font, you need to change the font-family. Something like this for bold text:

```css
.bold { font-family: "Verdana-Bold"; }
```

So it is better to have .bold, .light or .ultra-light styles and just extend them when needed: 

```css
.selector { @extend .bold; }
```