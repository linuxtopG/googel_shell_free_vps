# googel_shell_free_vps
### https://shell.cloud.google.com/
## stp1 log in https://shell.cloud.google.com/
## stp2 run shell
##stp3 update the paks
```
sudo apt update
```
```
sudo apt upgrade
```
##stp4 Install Required Packages
```
sudo apt update && sudo apt install -y xfce4 xfce4-goodies tightvncserver novnc websockify dbus-x11
```
#This command installs the XFCE desktop environment, the VNC server, noVNC, and necessary system libraries.

=======================================================================
##stp5  Set the VNC Password
#Create a password to secure your remote desktop session
```
vncpasswd
```
## Configure the Startup Script
```
mkdir -p ~/.vnc

echo "#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec dbus-launch startxfce4 &" > ~/.vnc/xstartup

chmod +x ~/.vnc/xstartup
```
##stp6 Start the Services
```
vncserver :1 -geometry 1280x720
```
### Start the noVNC Bridge
```
websockify --web /usr/share/novnc/ 8080 localhost:5901
```
### Access the Desktop
1- Click the Web Preview icon at the top right of the Cloud Shell window.
2- Select Preview on port 8080
3- vnc.html
4-A new browser tab will open. Click Connect and enter your VNC password
===============================================================================
#### 🛠️ Troubleshooting
CommandsTo stop the server: vncserver -kill :1T
o clear stuck lock files: 
```
sudo rm -rf /tmp/.X1-lock /tmp/.X11-unix/X1
```
