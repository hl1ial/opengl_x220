# Fix for Open GL on Intel HD Graphics 3000 - Windows 10

The drivers for Intel HD Graphics 3000 in Windows 10 does not expose all Open GL capabilities of the GPU. So software relying on Open GL features not present in Open GL 1.1 will not work. Using older versions of Windows or Linux might work since the chip have more features than the driver exposes.

The fix is to add a compatibility shim using the Windows ADK software.

## 1. Download and install Windows ADK

Link: https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install

Make sure to download the version that fits your Windows version, so if you have Windows 10 1803 choose the 1803 version and so on.

We only need the *Application Compatibility Tools* module, so choose this in the installer:

![adk-compatibility-tools](https://user-images.githubusercontent.com/7920910/55222684-d3eb2900-520c-11e9-901c-007f597caf83.png)

## 2. Use the Compatibility Administrator to create the fix

Make sure to start the relevant 32 or 64 bit version of the program, based on which type of software you want to create the compatibility fix for. So if the software you want to fix is 64 bit, use the 64 bit version of the tool.

Right click the *New Database* menu entry, and choose *Create New -> Application Fix...*

![new-application-fix](new-application-fix.png)

Give the fix a name, and browse for the executable file you want to add the fix for. In this example I am adding the fix for Python 3 64 bit programs, so I locate python.exe in C:\Program Files\Python37.

![new-application-fix-2](new-application-fix-2.png)

Then click Next. We do not choose anything on this *Compatibility Modes* page, so just click Next again.

![compatiblity-mode](compatibility-mode.png)

On the *Compatibility Fixes* page, scroll down and check the *Win81RTMVersionLie* option. Then click the *Parameters* button.

![compatibility-fix](compatibility-fix.png)

In the Parameters dialog box, *Module name:* field, type: ig4icd64.dll then click *Add* and then *OK*.

![compatibility-fix-2](compatibility-fix-2.png)

Click *Next* to the *Matching Information* page. Here, deselect all except the company name and product name options, then click *Finish*.

![compatibility-fix-3](compatibility-fix-3.PNG)

We have now created the fix needed, next is to save and install it.

![compatibility-fix-4](compatibility-fix-4.PNG)

Click the *Save* icon, and choose a name for the database. You will also need to choose a place to save the file and give the file a name, I just saved to the Documents folder.

![save-database](save-database.png)

When the database is saved, you can right click the database you just saved, and choose *Install*.

That should be it!

Credits to user **nonkonform1st** on YouTube and this video: https://www.youtube.com/watch?v=Yqe5cgthZH4