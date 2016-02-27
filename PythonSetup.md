# How to Set Python up in Windows

----
## First Things First
Download an installer for your preferred version of [Python] (https://www.python.org/downloads/). Then run the installer, but don't be to hasty!: Check the box "Add to PATH" to avoid going through the trouble of "Getting Windows to Recognize Python Exists". It's totally worth it.

*Hint: Make sure that the version you download is compatible with whatever you're working on.*

----
## Getting Windows to Recognize Python Exists
Most people can go straight from running the installer to being able to use python. However, us lucky folks on Windows have an extra step that likes to get in our way if we didn't check the box in the installer I mentioned above.

There *are* [instructions on java.com] (https://www.java.com/en/download/help/path.xml) on how to make things work on a Windows machine, but as of the writing of this markdown document, it doesn't have anything for Windows 10.

So here we go:

1) Find Control Panel.

This will seem almost impossible until you remember that you can just hit the windows button and type "control panel" and it'll pop up for you.

![Tada!] (ControlPanel.jpg)

2) Go to "System and Security"

![system] (SystemSecurity.jpg)

3) Then "System"

![system2] (System.jpg)

4) Then "Advanced System Settings"

*Note: You do need Administrator privileges to perform this action.*

![Advanced] (Advanced.jpg)

5) Then click "Environment Variables" (down at the bottom)

![Environment] (Environment.jpg)

6) Then under "System variables" ("1" in the picture below), click on "Path" ("2"), then click "Edit..." ("3").

![SystemPath] (SystemPath.jpg)

7) Then click "New" ("1" in the picture below) and type in the file path where you installed Python.

*If you just did the default install, it should be under "C:" or "C:\Users\[Username]\AppData\Local\Programs\". If not, just do a Windows search under "This PC".*

![Add] (AddPython.jpg)

8)Close your command prompts and reopen them

----
## Install pip
