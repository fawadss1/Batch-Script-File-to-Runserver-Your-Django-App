# Batch Script to Runserver Your Django App

This batch script will get the IP Adress of your computer then run the server based on the IP Address.
<br>The same result with if you run: `python manage.py runserver your_ip_address:80`

# How to Use
1. put this script file in your django app root (in the same level with your manage.py). 
2. double click the script file to run it.
3. the cmd window will pop up immediately, there will be IP address shown, you can access the app with that IP address.

The IP Address shown in the command prompt is the url of your app. You have to make sure your device is in the same network with the computer server.
<br><strong>Important to note:</strong> if you're using virtual environment in your app, you need to adjust your virtual environment folder name or change the `venv\Scripts\activate` in the script with your virtual environment's path.


===========================================================================

# Line 1
`@ECHO OFF,` is to disable the echoing so that it will not display the content of the batch script.

# Line 2
The purpose of the command in this line is to get IP address from ipconfig command and then set it to a variable _IPAddress.

`FOR /F “delims=: tokens=2” %%a in (‘ipconfig ^| find “IPv4”’) do set _IPAddress=%%a`

# Line 3
There are actually three commands in this line.

`cd /d %~dp0 & “venv\Scripts\activate” & python manage.py runserver %_IPAddress%:80`
`cd /d %~dp0,` is to direct us to where the batch file is located, which is the root of our app.
`venv\Scripts\activate` is to activate the virtual environment. Since we’re already directed to the root of our app, we don’t need to write the full path.
after the virtual environment activated, we run the server with `python manage.py runserver %_IPAddress%:80` While `%_IPAddress%` is the variable where we put our IP address.

# Line 4
The last line `cmd /k` is to prevent the command prompt window from closing.

