
# x11VNC
sudo apt-get install x11vnc

sudo nano /lib/systemd/system/x11vnc.service

# Nota: yourPassword is the password.
# Coloar o texto abaixo:

[Unit]
Description=x11vnc service
After=display-manager.service network.target syslog.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -forever -display :0 -auth guess -passwd yourPassword
ExecStop=/usr/bin/killall x11vnc
Restart=on-failure

[Install]
WantedBy=multi-user.target



# Os comandos abaixo vão reinciar e habilitar o serviço.

systemctl daemon-reload
systemctl enable x11vnc.service
systemctl start x11vnc.service
systemctl status x11vnc.service


x11vnc status


sudo reboot

# 1: Recarregar o serviço:

sudo systemctl daemon-reload

# 2. Habilitar o serviço no boot:

sudo systemctl enable x11vnc.service

# 3. Iniciar o serviço:

sudo systemctl start x11vnc.service
