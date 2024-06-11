
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


--------------------------------------------------------------------------

# x11VNC MX Linux
#1
sudo apt install x11vnc
#2
x11vnc -storepasswd

# Nota: Digitar a senha 2 vezes.
#3
Criar pasta mkdir -p (~/.desktop-session/startup) definir startup como executável (chmod +x)

#4
Escrever no arquivo startup 
x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/terminal/.vnc/passwd -rfbport 5900 -shared -display :0 >/dev/null 2>&1 &

#5
Adicionar scripit startup a inicialização da seção utilizando a aplicação Sessão e Inicialização

#6
habilitar regra no firewall
sudo ufw allow 5900

sudo service x11vnc status


sudo reboot

# 1: Recarregar o serviço:

sudo service x11vnc start

# 2. Habilitar o serviço no boot:

sudo service x11vnc enable



