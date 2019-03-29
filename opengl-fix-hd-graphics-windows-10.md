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

![new-application-fix](https://user-images.githubusercontent.com/7920910/55222721-e2394500-520c-11e9-87fe-ea399bcc5a56.png)

Give the fix a name, and browse for the executable file you want to add the fix for. In this example I am adding the fix for Python 3 64 bit programs, so I locate python.exe in C:\Program Files\Python37.

![new-application-fix-2](https://user-images.githubusercontent.com/7920910/55222727-e4030880-520c-11e9-8eb0-80d975ee423e.png)

Then click Next. We do not choose anything on this *Compatibility Modes* page, so just click Next again.

![compatibility-mode](https://user-images.githubusercontent.com/7920910/55222713-dea5be00-520c-11e9-84e9-0429cff09df6.png)

On the *Compatibility Fixes* page, scroll down and check the *Win81RTMVersionLie* option. Then click the *Parameters* button.

![compatibility-fix](https://user-images.githubusercontent.com/7920910/55222693-d6e61980-520c-11e9-93c4-ae24985a451c.png)

In the Parameters dialog box, *Module name:* field, type: ig4icd64.dll then click *Add* and then *OK*.

![compatibility-fix-2](https://user-images.githubusercontent.com/7920910/55222694-d8174680-520c-11e9-9a31-04d17b6d82f3.png)

Click *Next* to the *Matching Information* page. Here, deselect all except the company name and product name options, then click *Finish*.

![compatibility-fix-3](https://user-images.githubusercontent.com/7920910/55222702-da79a080-520c-11e9-9ed2-76b3f5f2336c.png)

We have now created the fix needed, next is to save and install it.

![compatibility-fix-4](https://user-images.githubusercontent.com/7920910/55222706-dc436400-520c-11e9-97cf-f2fc2c9bedf7.PNG)

Click the *Save* icon, and choose a name for the database. You will also need to choose a place to save the file and give the file a name, I just saved to the Documents folder.

![save-database](https://user-images.githubusercontent.com/7920910/55222736-e6656280-520c-11e9-831d-0b629ed7bab2.png)

When the database is saved, you can right click the database you just saved, and choose *Install*.

That should be it!

Credits to user **nonkonform1st** on YouTube and this video: https://www.youtube.com/watch?v=Yqe5cgthZH4