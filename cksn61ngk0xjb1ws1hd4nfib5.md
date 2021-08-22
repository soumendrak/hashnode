## Run Nginx as a service in Windows


NSSM is the best tool to run Nginx as a service. You can follow this SO answer for more details.
If due to software restrictions or any other trouble, you do not want to use any external 3rd party software then you can deploy any of these two methods.

* Windows Task Scheduler

* Windows startup shortcut

**Windows Task Scheduler**

* As mentioned in [this answer](https://stackoverflow.com/a/39802422/5014656) prepare one start.bat file.

```
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


* Put this file where nginx.exe is present.

* Open windows task scheduler and set up the task as described in [this answer](https://superuser.com/a/403597/467698) to run it indefinitely.

* Do not forget to run this task as the highest privilege with the system account, more details can be found [here](https://superuser.com/a/770439/467698).

* Make the task to start daily at a certain time, through the bat file it will check whether the service is already running to avoid creating multiple nginx.exe instances.

* If due to some reason Nginx shuts down, within 5 minutes it will start.

**Windows Startup shortcut**

* Create one shortcut of nginx.exe and put it in the startup folder of Windows.

* Follow [this answer](https://superuser.com/a/489778/467698) to find your startup location.

* Nginx will run automatically whenever you log in to the system.

* This one is the easiest. However, it is dependent on user profile i.e. if you are running Nginx on a server, it will run only for your user account, when you log off it stops.

* This is ideal for dev environment.