# Linux-commands<img height="40px" align="right" src="https://upload.wikimedia.org/wikipedia/commons/3/35/Tux.svg" alt=""/>

---
## Raspberry pi: <img height="40px" align="right" src="https://www.vectorlogo.zone/logos/raspberrypi/raspberrypi-icon.svg" alt=""/>                          

<details>    
<summary><ins>Globale install for opencv:</ins></summary>    
<pre><code class="language-shell"> sudo apt install python3-opencv     
</code></pre> 
</details>
 <details>
 <summary><ins>venv install opencv:</ins></summary>
<pre><code class="language-shell"> pip install --upgrade pip
</code></pre> 
<pre><code class="language-shell"> pip install opencv-python
</code></pre> 
✴ To track the process:
<pre><code class="language-shell"> pip install opencv-python --verbose 
</code></pre> 
</details>
 <details>
 <summary><ins>Install pyaudio:</ins></summary>
<pre><code class="language-shell">pip install pyaudio
</code></pre> 
✴ need to install portaudio19-dev:
<pre><code class="language-shell">sudo apt install portaudio19-dev
</code></pre> 
✴ If you are in lite os install:
<pre><code class="language-shell">sudo apt install pulseaudio
</code></pre> 
</details>
 <details>
 <summary><ins>Open audio sound:</ins></summary>
<pre><code class="language-shell">alsamixer
</code></pre> 
</details>
 <details>
 <summary><ins>Copy folder from pi to pc:</ins>(example)</summary>
<pre><code class="language-shell">scp -r pi@192.168.68.150:~/MUSICAL_DOOR_BELL /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR
</code></pre> 
</details>
 <details>
 <summary><ins>Copy file from pi to pc:</ins>(example)</summary>
<pre><code class="language-shell">scp pi@192.168.68.150:~/MUSICAL_DOOR_BELL/main.py /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR
</code></pre> 
 </details>
 <details>
 <summary><ins>Copy folder from pc to pi:</ins>(example)</summary>
<pre><code class="language-shell">scp -r /home/user/Documents/my_folder pi@192.168.1.100:/home/pi/
</code></pre> 
 </details>
 <details>
 <summary><ins>Copy file from pc to pi:</ins>(example)</summary>
<pre><code class="language-shell">scp /home/user/Documents/example.txt pi@192.168.1.100:/home/pi/
</code></pre> 
 </details>
<details>
 <summary><ins>Add you script at startup:</ins></summary>
<pre><code class="language-shell">sudo crontab -e
</code></pre> 
✴ Add this to the end:(example)
<pre><code class="language-shell">@reboot python3 /home/pi/MUSICAL_DOOR_BELL/main.py &
</code></pre> 
✴ If you want to add log-file:(example)
<pre><code class="language-shell">@reboot sudo /usr/bin/python3 /home/pi/MUSICAL_DOOR_BELL/main.py > /home/pi/MUSICAL_DOOR_BELL/logfile.log 2>&1 &
</code></pre> 
</details>
 <details>
 <summary><ins>Better way to run on startup script:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/rc.local
</code></pre> 
✴ If you want delay
<pre><code class="language-shell">sleep 30
</code></pre> 
✴ Add this to the end:(example)
<pre><code class="language-shell">su -c "python3 /path/to/your/script.py > /path/to/your/logfile.log 2>&1" pi &
</code></pre> 
✴ if you want to run chrome in kiosk mode:(example)
<pre><code class="language-shell">su -c "/usr/bin/chromium-browser --kiosk --disable-session-crashed-bubble --disable-infobars http://localhost:5555" pi
</code></pre> 
✴ Update permission:
<pre><code class="language-shell">sudo chmod +x /etc/rc.local
</code></pre> 
✴ run as pi user
<pre><code class="language-shell">su - pi -c "authbind --deep /usr/bin/python3 /home/pi/Documents/knowpet/main.py >> /home/pi/Documents/knowpet/logfile.log 2>&1 &"
</code></pre> 
</details>
 <details>
 <summary><ins>Run app with UI in startup use this:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
</code></pre> 
✴ Add this in the end:(example)
<pre><code class="language-shell">@/usr/bin/python /home/pi/example.py
</code></pre> 
</details>
 <details>
 <summary><ins>Hide the taskbar command this line:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
</code></pre> 
✴ Command this line:
<pre><code class="language-shell">#@lxpanel --profile LXDE-pi
</code></pre> 
</details>
 <details>
 <summary><ins>Chnage splash screen:</ins></summary>
  <div>✴ First change the splash image in what you like in this dir:
	<ul>/usr/share/plymouth/themes/pix</ul>
</div>
✴ Then run this command:
<pre><code class="language-shell">sudo plymouth-set-default-theme --rebuild-initrd pix
</code></pre> 
<div>✴ Disable rainbow splash:
	<ul>Add or edit this line:</ul>
</div>
<pre><code class="language-shell">disable_splash=1 to /boot/config.txt
</code></pre> 
✴ To remove the blinking curse add this:
<pre><code class="language-shell">vt.global_cursor_default=0 
</code></pre> 
✴ To:
<pre><code class="language-shell">/boot/cmdline.txt
</code></pre> 
✴ Mute kernel logs (only show critical errors) Add:
<pre><code class="language-shell">loglevel=3
</code></pre> 
✴ To:
<pre><code class="language-shell">/boot/cmdline.txt 
</code></pre> 
</details>
 <details>
 <summary><ins>Run GUI script from SSH:</ins></summary>
✴ Run this command:
<pre><code class="language-shell">export DISPLAY=:0
</code></pre> 
✴ Now you can run the script
</details>
 <details>
 <summary><ins>Run GUI script:</ins></summary>
✴ Add to python script:
<pre><code class="language-shell">os.environ["DISPLAY"] = ":0"
</code></pre> 
✴ Now you can run the script
</details>
<details>
 <summary><ins>Install picamera2:</ins></summary>
✴ Run this command:
<pre><code class="language-shell">sudo apt install -y python3-picamera2
</code></pre> 
</details>
<details>
 <summary><ins>Make raspberry discoverable by local network:</ins></summary>
✴ Run this command:
<pre><code class="language-shell">sudo nano /etc/avahi/avahi-daemon.conf
</code></pre> 
✴ In [server] section uncomment and modify this line to your desired hostname:
<pre><code class="language-shell">#host-name=foo
</code></pre>
✴ Run this command:
<pre><code class="language-shell">sudo service avahi-daemon restart
</code></pre>
✴ To discover it:
<pre><code class="language-shell">ping hostname.local
</code></pre> 
</details>
<details>
 <summary><ins>Set a static IP address for Raspberry Pi:</ins></summary>
✴ Run this command:
<pre><code class="language-shell">sudo nano /etc/dhcpcd.conf
</code></pre> 
✴ In end of the file add the following lines:
<pre><code class="language-shell">interface wlan0
static ip_address=192.168.1.100/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1
</code></pre>
✴ Run this command:
<pre><code class="language-shell">sudo service dhcpcd restart
</code></pre>
</details>
<details>
 <summary><ins>Permanently hide mouse pointer on Raspberry pi:</ins></summary>
✴ Run this command:
<pre><code class="language-shell">sudo nano /etc/lightdm/lightdm.conf
</code></pre> 
✴ Add this to the file after [Seat:*]:
<pre><code class="language-shell">xserver-command = X -nocursor
</code></pre> 
</details>
<details>
 <summary><ins>Bind flask to port 80:</ins></summary>
✴ Install authbind:
<pre><code class="language-shell">sudo apt install authbind
</code></pre> 
✴ Configure access to port 80:
<pre><code class="language-shell">sudo touch /etc/authbind/byport/80
sudo chmod 777 /etc/authbind/byport/80
</code></pre> 
✴ For security:
<pre><code class="language-shell">sudo chmod 550 /etc/authbind/byport/80
sudo chgrp {groupname} /etc/authbind/byport/80
sudo usermod -a -G {groupname} {username}
</code></pre> 
✴ To run:
<pre><code class="language-shell">authbind --deep python3 main.py
</code></pre> 
</details>
<details>
 <summary><ins>Create hotspot network on Raspberry pi:</ins></summary>
✴ Create hotspot for wifi_device:
<pre><code class="language-shell">sudo nmcli device wifi hotspot ssid {hotspot_name} password {hotspot_password} ifname {wifi_device}
</code></pre> 
✴ Example:
<pre><code class="language-shell">sudo nmcli device wifi hotspot ssid Home_5GHz password 12345678 ifname wlan0
</code></pre> 
✴ To get hotspot_UUID:
<pre><code class="language-shell">nmcli connection
</code></pre>
✴ Set autoconnect to hotspot:
<pre><code class="language-shell">sudo nmcli connection modify {hotspot_UUID} connection.autoconnect yes connection.autoconnect-priority 100
</code></pre> 
✴ To verify:
<pre><code class="language-shell">nmcli connection show {hotspot_UUID}
</code></pre> 
🚨 Important to let DNS working and internet sharing:
<pre><code class="language-shell">sudo nmcli connection modify {hotspot_UUID} ipv4.addresses 192.168.4.1/24 ipv4.method shared
</code></pre> 
</details>

<details>
 <summary><ins>Set Git username and email:</ins></summary>
<pre><code class="language-shell">git config --global user.name "Your Name"
</code></pre> 
<pre><code class="language-shell">git config --global user.email "your.email@example.com"
</code></pre> 
</details>

<details>
 <summary><ins>Kiosk mode:</ins></summary>
✴ 🚨 Note: Install this if you are runing in raspberry pi 5
<pre><code class="language-shell">sudo apt install gldriver-test
</code></pre> 	
✴ Update:
<pre><code class="language-shell">sudo apt update
</code></pre> 
<pre><code class="language-shell">sudo apt upgrade
</code></pre> 
✴ Install graphics libraries:
<pre><code class="language-shell">sudo apt-get install --no-install-recommends xserver-xorg x11-xserver-utils xinit openbox
</code></pre> 
✴ Chromium installation:
<pre><code class="language-shell">sudo apt-get install --no-install-recommends chromium-browser
</code></pre> 
✴ Chromium installation in debian:
<pre><code class="language-shell">sudo apt-get install --no-install-recommends chromium
</code></pre> 
✴ Openbox configuration:
<pre><code class="language-shell">sudo nano /etc/xdg/openbox/autostart
</code></pre>
✴ Replace the contents of the file with the following:
<pre><code class="language-shell">
# Start Chromium in kiosk mode
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Preferences
/usr/bin/chromium --disable-infobars --kiosk 'http://your-url-here' &
</code></pre> 
✴ If you are in debian Replace the contents of the file with the following:
<pre><code class="language-shell">
# Start Chromium in kiosk mode
# Disable any form of screen saver / screen blanking / power management
xset s off
xset s noblank
xset -dpms
# Allow quitting the X server with CTRL-ALT-Backspace
setxkbmap -option terminate:ctrl_alt_bksp
# Start Chromium in kiosk mode
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Pr>
(sleep 5 && /usr/bin/chromium --disable-infobars --kiosk 'https://google.com') &
</code></pre> 
✴ If you are in debian and you want to rotate screen & touch:
<pre><code class="language-shell">
# Start Chromium in kiosk mode
# Rotate screem and detect screen automaticaly 
xrandr --output $(xrandr | grep -w "connected" | grep "HDMI" | awk '{print $1}') --rotate right &
# Apply touchscreen transformation for right rotation
(sleep 3 && xinput set-prop 8 "Coordinate Transformation Matrix" 0 1 0 -1 0 1 0 0 1) &
(sleep 3 && xinput set-prop 9 "Coordinate Transformation Matrix" 0 1 0 -1 0 1 0 0 1) &
# Apply touchscreen transformation for left rotation
#(sleep 3 && xinput set-prop 8 "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1) &
#(sleep 3 && xinput set-prop 9 "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1) &
# Disable any form of screen saver / screen blanking / power management
xset s off
xset s noblank
xset -dpms
# Allow quitting the X server with CTRL-ALT-Backspace
setxkbmap -option terminate:ctrl_alt_bksp
# Start Chromium in kiosk mode
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'
sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Pr>
(sleep 5 && /usr/bin/chromium --disable-infobars --kiosk 'https://google.com') &
</code></pre> 
✴ Autologin:
<pre><code class="language-shell">sudo mkdir -p /etc/systemd/system/getty@tty1.service.d
</code></pre>
<pre><code class="language-shell">sudo nano /etc/systemd/system/getty@tty1.service.d/override.conf
</code></pre>
✴ Add the following:
<pre><code class="language-shell">
[Service]
ExecStart=
ExecStart=-/sbin/agetty --autologin dz --noclear %I $TERM
</code></pre>
🚨 Note: dz = username<br>
✴ Update service:
<pre><code class="language-shell">sudo systemctl daemon-reload
</code></pre>
<pre><code class="language-shell">sudo systemctl restart getty@tty1
</code></pre>
🚨 Automatically Run startx on Login:
<pre><code class="language-shell">echo "if [ -z "\$DISPLAY" ] && [ \$(tty) = /dev/tty1 ]; then startx -- -nocursor; fi" >> ~/.profile
</code></pre>

</details>

<details>
 <summary><ins>Set DISPLAY variable:</ins></summary>
<pre><code class="language-shell">export DISPLAY=:0
</code></pre> 
</details>

<details>
 <summary><ins>Connect to Wi-Fi using nmcli variable:</ins></summary>
✴ List Available Wi-Fi Networks:
<pre><code class="language-shell">nmcli device wifi list ifname wlanXX
</code></pre> 
✴ Connect to a Wi-Fi Network:
<pre><code class="language-shell">sudo nmcli device wifi connect "SSID" password "password" ifname wlanXX
</code></pre> 
✴ Verify Connection:
<pre><code class="language-shell">nmcli connection show --active
</code></pre> 
✴ Check the connection name:
<pre><code class="language-shell">nmcli connection show
</code></pre> 
✴ Set the connection to auto-connect:
<pre><code class="language-shell">sudo nmcli connection modify "connection_name" connection.autoconnect yes
</code></pre> 
✴ Verify the auto-connect setting:
<pre><code class="language-shell">nmcli connection show "connection_name"
</code></pre> 
</details>

<details>
 <summary><ins>Add font to debian:</ins></summary>
✴ Create the fonts directory:
<pre><code class="language-shell">sudo mkdir -p /usr/share/fonts/truetype/custom
</code></pre> 
✴ Copy your font files to this directory:
<pre><code class="language-shell">sudo cp /path/to/font.ttf /usr/share/fonts/truetype/custom/
</code></pre> 
✴ Update the font cache
<pre><code class="language-shell">sudo fc-cache -f -v
</code></pre> 
✴ Verify the Installation:
<pre><code class="language-shell">fc-list | grep "FontName"
</code></pre> 
</details>

<details>
 <summary><ins>Add permissions to access USB devices:</ins></summary>
✴ Create a new udev rule file:
<pre><code class="language-shell">sudo nano /etc/udev/rules.d/99-usb.rules
</code></pre> 
✴ Add the following line to give all users permission to access USB devices:
<pre><code class="language-shell">SUBSYSTEM=="usb", MODE="0666"
</code></pre> 
✴ Save the file and reload the udev rules:
<pre><code class="language-shell">sudo udevadm control --reload-rules
</code></pre> 
✴ Alternatively, if you need specific access to a particular USB device, you can add a rule based on the device's vendor and product ID. Replace 1234 and 5678 with the actual vendor and product IDs:
<pre><code class="language-shell">SUBSYSTEM=="usb", ATTR{idVendor}=="1234", ATTR{idProduct}=="5678", MODE="0666"
</code></pre> 
🚨 Note: log out and log back in
</details>


<details>
 <summary><ins>Run Flask in HTTPS with Certificate</ins></summary>

### 🚀 Deploy Flask App with Duck DNS, Gunicorn, Nginx & HTTPS (Let's Encrypt)

<details>
 <summary><ins>1. Run Flask App Behind Gunicorn</ins></summary>
<pre><code class="language-shell"># In your project folder:
pip install gunicorn

# Run Gunicorn (use your actual filename if not app.py):
gunicorn -w 4 -b 127.0.0.1:8000 app:app

# 'app:app' means 'filename:Flask instance'
# Example: if your file is 'main.py' and your Flask instance is 'app', use 'main:app'
</code></pre>

You can also create a `systemd` service later to run it on boot.
</details>

<details>
 <summary><ins>2. Configure Nginx for HTTPS (DuckDNS)</ins></summary>
<pre><code class="language-shell"># Create or edit your Nginx config:
sudo nano /etc/nginx/sites-available/shopi
</code></pre>

Paste this:

```nginx
server {
    listen 80;
    server_name shopi.duckdns.org;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

Enable the config and reload Nginx:

<pre><code class="language-shell">sudo ln -s /etc/nginx/sites-available/shopi /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
</code></pre>
</details>

<details>
 <summary><ins>3. Get a Free HTTPS Certificate with Certbot</ins></summary>
Make sure:
- Your domain (e.g., `shopi.duckdns.org`) points to your public IP
- Ports **80** and **443** are forwarded to your Raspberry Pi

Then run:

<pre><code class="language-shell">sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d shopi.duckdns.org
</code></pre>

Certbot will:
- Verify your domain
- Get an HTTPS certificate
- Automatically update your Nginx config
</details>

<details>
 <summary><ins>4. Done! Your Flask App is Live at:</ins></summary>
<pre><code class="language-text">https://shopi.duckdns.org
</code></pre>
</details>

</details>


---
## Linux:<img height="40px" align="right" src="https://www.debian.org/logos/openlogo-nd.svg" alt=""/>    

 1. keyboard shortcuts  : 
	-  hibernate : sudo systemctl hibernate (Shift + Alt + H)
	-  new-window : nautilus --new-window (Super + E)
	-  reboot : sudo reboot now (Shit + Alt + R)
	-  shutdown : sudo shutdown now (Shit + Alt + S)
	-  open terminal : gnome-terminal (Ctrl + Alt + T)
	-  enable gnome extensions : gnome-extensions enable hanabi-extension@jeffshee.github.io (Ctrl + Alt + L)
	-  disable gnome extensions : gnome-extensions disable hanabi-extension@jeffshee.github.io (Ctrl + Alt + L)
	
2. Update Swap for hibernation.
	- sudo nano /etc/fstab
	- add this : UUID= < UUID >          none            swap    sw              0       0
	-  <font color="#2DC26B">sudo</font> nano /etc/default/grub 
		  edit this : GRUB_CMDLINE_LINUX="... resume=UUID=< UUID >"
	-  <font color="#2DC26B">sudo</font> update-grub
	-  <font color="#2DC26B">sudo</font> nano /etc/initramfs-tools/conf.d/resume
		  edit this : RESUME=UUID=< UUID >
	-  <font color="#2DC26B">sudo</font> update-initramfs -u
4. allow users to run commands without entering a password : 
	-  <font color="#2DC26B">sudo</font> visudo
	  Add the following line at the end of the file : < username > ALL=(ALL) NOPASSWD: /sbin/shutdown 
		  ps: you can get command path by using whereis shutdown or other commands
