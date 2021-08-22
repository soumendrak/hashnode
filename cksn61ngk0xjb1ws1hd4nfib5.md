## Run Nginx as a service in Windows platform


NSSM is the best tool to run Nginx as a service. You can follow this SO answer for more details.
If due to software restrictions or any other trouble, you do not want to use any external 3rd party software then you can deploy any of these two methods.

* Windows Task Scheduler

* Windows startup shortcut

**Windows Task Scheduler**

* As mentioned in [this answer](https://stackoverflow.com/a/39802422/5014656) prepare one start.bat file.

### start.bat

```bash
@ECHO OFF
REM Start Nginx
tasklist /FI "IMAGENAME eq nginx.exe" 2>NUL | find /I /N "nginx.exe">NUL
IF NOT "%ERRORLEVEL%"=="0" (
   REM Nginx is NOT running, so start it
   c:
   cd \nginx
   start nginx.exe
   ECHO Nginx started.
) else (
   ECHO Nginx is already running.
)
```

### stop.bat

```bash
@ECHO OFF
REM Stop Nginx
tasklist /FI "IMAGENAME eq nginx.exe" 2>NUL | find /I /N "nginx.exe">NUL
IF "%ERRORLEVEL%"=="0" (
   REM Nginx is currently running, so quit it
   c:
   cd \nginx
   nginx.exe -s quit
   ECHO Nginx quit issued.
) else (
   ECHO Nginx is not currently running.
)
```

* Put this file where nginx.exe is present.

* Open windows task scheduler and set up the task as described in [this answer](https://superuser.com/a/403597/467698) to run it indefinitely.

> ### 1. Add a trigger: 
> 
> ![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629636047855/wMsFOF2gV.png)
> Make sure to set the current date and 00:00:00 as the start time

> ### 2. Make sure the task is run as soon as possible if the start was missed: 

> ![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629636097369/UUuBxbh24.png)

* Do not forget to run this task as the highest privilege with the system account, as described [here](https://superuser.com/a/770439/467698).

> 1. Open Task Scheduler
> 2. Create a new task
> 3. In the "General" tab - ensure the following settings are entered:
>     - "Run whether the user is logged on or not"
>     - "Run with highest privileges"
>     - "Configure For" (your operating system)
> 4. In the "Triggers" tab, when adding a trigger (schedule) - ensure that the "Enabled" checkbox is checked
> 
> The other tabs need to be looked at as well (actions etc) - but these are the options you should specify when trying to ensure a task runs regardless of which user is logged in, and without the UAC prompts.  
> When saving the task, you will be prompted to enter a username and password - this username and password is the user that will be used to execute the task.  If you are running the task with "highest privileges" you will need to make sure this is an admin account.

* Make the task to start daily at a certain time, through the bat file it will check whether the service is already running to avoid creating multiple nginx.exe instances.

* If due to some reason Nginx shuts down, within 5 minutes it will start.

**Windows Startup shortcut**

* Create one shortcut of nginx.exe and put it in the startup folder of Windows.

* Follow [this answer](https://superuser.com/a/489778/467698) to find your startup location.

> It can be found here:
> ``` 
> C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
> ```
> or easier to access with this command in the Run <kbd>Win</kbd>+<kbd>R</kbd> prompt:
> ```
> shell:startup
> ```
> ![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629636447317/PHDbdxpDg.png)
> 
> [Here](http://www.addictivetips.com/windows-tips/where-is-startup-folder-how-to-edit-startup-items-in-windows-8/) is even more explanations of how accessing/viewing the startup folder.

* Nginx will run automatically whenever you log in to the system.

* This one is the easiest. However, it is dependent on the user profile i.e. if you are running Nginx on a server, it will run only for your user account, when you log off it stops.

* This is ideal for the dev environment.