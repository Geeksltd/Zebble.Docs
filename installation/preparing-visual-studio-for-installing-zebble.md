[1]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/1.png "Zebble-VisualStudio"
[2]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/2.png "Zebble-VisualStudio"
[3]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/3.png "Zebble-VisualStudio"
[4]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/4.png "Zebble-VisualStudio"
[5]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/5.png "Zebble-VisualStudio"
[6]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/6.png "Zebble-VisualStudio"
[7]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/7.png "Zebble-VisualStudio"
[8]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/8.png "Zebble-VisualStudio"
[9]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/9.png "Zebble-VisualStudio"
[10]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/installation/preparing-visual-studio-for-installing-zebble/10.png "Zebble-VisualStudio"

### PREPARING VISUAL STUDIO FOR INSTALLING ZEBBLE

#### Install Extention
First of all, you need to install a version of **Microsoft Visual Studio** on your personal device. You can check out [Installing-introduction](http://zebble.net/docs/installing-introduction) to acquire information about the other prerequisites.

Next steps are

1. Install **Zebble Extension** To do this, go ahead and open “Tools”:

![1]

2. In the menu opened, choose **“Extensions and Updates”**:

![2]

3. On the **“Online”** tab, search **“Zebble”**:

![3]

4. Press the **“Download”** button to download Zebble:

![4]

5. You need to close Visual Studio and click on **“Modify”** button to install Zebble.
Congrats. You just installed Zebble extension. To make sure Zebble is installed correctly, do the aforementioned
steps to open “Online” tab again. Now you should be seeing something like the figure below.


![5]
 

6. Now, it’s time to create a Zebble project. After doing that, you will see a **“READ-ME-NOW!!!!!!!!!!!!.txt”** file:

![6] 
 

7. You should do its instructions step by step. To run a bat file, you can create an external tool called "Run batch file".
   1. Go to Tools-> External Tools, create a new and then, use the following parameters:

```
 Command: CMD.EXE
 Arguments: /c "$(ItemPath)"
 Initial directory: $(ItemDir)
```

**Attention:** DO NOT Check the "use output window" check box.


Press “Apply” to create the command.

 
![7]


8. Note where the new command appeared in the list of commands. The external commands are numbered from 1.
starting below the divider bar. To make it easy to remember you can move the new command to the top, to be the
first command in the list.
Now go to **Tools -> Customize** and select the **commands** tab. Select the **“Context menu”** radio button and select
**"Project and Solution Context menus | Item”**. Use **"Add Command..."** to add a new command.

 
![8]
 

9. In the Categories list,
select **"Tools"**. From the commands select the **"External Command #"** in which the “#” sign represents the position
of the "Run Batch file" custom command you noted the number of, above.

You can move it to the right on the list, add keyboard shortcuts and so on.
Done. You can close the dialogue now.

 
![9]
 

10. Finally, right click on the batch file. You will see a "Run batch file" menu item. This will execute the batch file and
show its output in the VS Output window.
After doing all steps in the READ-ME-NOW!!!!!!!!!!!!.txt file, if you run the project you will see something like
this:

 
![10]
 

If you want to know how to create a task list in Zebble, please check out [create a task list in Zebble](http://zebble.net/docs/creating-task-list-in-zebble)