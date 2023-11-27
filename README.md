# x11VNC
x11VNC install linux mint (LMDE)

1. Install x11vnc:

sudo apt-get -y install x11vnc

2. Create the directory for the password file:

sudo mkdir /etc/x11vnc

3. Create the encrypted password file:

sudo x11vnc --storepasswd /etc/x11vnc/vncpwd

You will be asked to enter and verify the password.  Then press Y to save the password file.

4. Create the systemd service file for the x11vnc service:

sudo xed /lib/systemd/system/x11vnc.service

Copy/Paste this code into the empty file:

[Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -noxdamage -repeat -rfbauth /etc/x11vnc/vncpwd -rfbport 5900 -shared

[Install]
WantedBy=multi-user.target

5: Reload the services:

sudo systemctl daemon-reload

6. Enable the x11vnc service at boot time:

sudo systemctl enable x11vnc.service

7. Start the service:

Reboot or

sudo systemctl start x11vnc.service
