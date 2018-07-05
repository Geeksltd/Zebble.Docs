
### HOW TO DEBUG ZEBBLE.EXE?

The Zebble.exe process is executed for various Zebble build operations, and it's invoked regularly during compilation.

Now imagine that you want to get your hands dirty in the Zebble engine and update the source code of ZebbleExe tool. As the EXE file is automatically executed in the project during the build process, there is no obvious point to attach a debugger to it - so you may be wondering how you can debug it? 

- Open the Zebble solution source in Visual Studio.
- Mark ZebbleExe as the starting project.
- Right-click ZebbleExe and go to > Properties > Debug
  - In **Working Directory**, type C:\Projects\MyAppProject\Run\Android.
  - In the **Command line arguments**:  type generate,  or any other command that you want to debug.
- Add a breakpoint at Program.cs > ProcessCommand().
- Press F5 to run with debugger.