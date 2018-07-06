[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-1.png
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-2.png
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-3.png
[4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-4.png
[5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-5.png
[6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/tutorials/10-6.png

### ALERTS, DIALOG, PROMPT AND TOAST

In this lesson, you will learn how to very quickly show simple messages to the user, or to take confirmation or text input using the Alert class.

[Download this video directly](https://drive.google.com/file/d/0B3EED8dgociySUdkMmFmWXpRcms/view?usp=sharing)

[![INTRODUCTION TO ZEBBLE](https://github.com/Geeksltd/Zebble.Docs/blob/master/assets/tutorials/1.png?raw=true)](https://youtu.be/arUIdT1r14c)

----------------------------------------------- 

 
#### Simple Alert


By default, it gives you a single button named "OK". But you can also use the other overloads of the Alert class to define your own button(s).

```csharp
await Alert.Show("some message");
```
 
![1]
 

#### Alert with title


If your message is long, then you can use another override to show a message in the title. This allows you to use the title to display the main point to the user and then provide more details if the users interested in learning more.

```csharp
wait Alert.Show("some title", "some message");
```
 
![2]


#### Alert with buttons


By default, Alert.Show() will display the single OK button. But you can customize and change the button text and allow users to select one. Each option will be a key value pair where the key is the text of the button and the value can be any type.

```csharp
var result = await Alert.Show(
"The title",
"My Message",
KeyValuePair.of("Option 1", 1),
KeyValuePair.of("Option 2", 2),
KeyValuePair.of("Option 3", 3));
```
 
![3]
 

#### Confirm


The Alert class has another method named Confirm() which is a simple shortcut to creating and alert by Confirm and Cancel buttons, representing True and False.  

```csharp
var confirmed=await Alert.Confirm("Are you sure?");
if (confirmed)
{
// ...
}
```
  
![4]
 
#### Prompt


You can use Alert.Prompt() function to get value from users. If user do not input any data, it returns Null value.

```csharp 
var input=await Alert.Prompt(
"My title",
"Please enter...");
// Use input ...
```
 
![5] 

#### Toast messages


**Toast** is a little text popup to show some notification message to the user in a non-intrusive way. It automatically disappears after a few seconds.

Unlike a message box, it doesn't block the user experience and force the user to tap OK.

By default, it shows an OK button next to your message, but you can optionally remove that.
 

![6]


#### Examples:

```csharp
await Alert.Toast("my message");
```

If you want to show the message without OK button, you should set **showButton** property on **false** . 

```csharp
await Alert.Toast("my message", showButton: false);
```
