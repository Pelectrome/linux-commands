# Linux-commands<img height="40px" align="right" src="https://upload.wikimedia.org/wikipedia/commons/3/35/Tux.svg" alt=""/>

---
## Raspberry pi: <img height="40px" align="right" src="https://www.vectorlogo.zone/logos/raspberrypi/raspberrypi-icon.svg" alt=""/>                          

#### **<ins>Globale install for opencv:</ins>**
 <details>
 <summary>Details</summary>


```shell
sudo apt install python3-opencv
```
</details>

#### **<ins>venv opencv install opencv:</ins>**
 <details>
 <summary>Details</summary>


```shell
pip install --upgrade pip
```

```shell
pip install opencv-python
```

- To track the process:

```shell
pip install opencv-python --verbose 
``` 
</details>

#### **<ins>Open audio sound:</ins>**
 <details>
 <summary>Details</summary>


```shell
alsamixer
```
</details>

#### **<ins>Copy folder from pi to pc:</ins>**(example)
 <details>
 <summary>Details</summary>


```shell
scp -r pi@192.168.68.150:~/MUSICAL_DOOR_BELL /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR
```
</details>

#### **<ins>Copy file from pi to pc:</ins>**(example)
 <details>
 <summary>Details</summary>


```shell
scp pi@192.168.68.150:~/MUSICAL_DOOR_BELL/main.py /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR
```
 </details>

#### **<ins>Add you script at startup:</ins>**
 <details>
 <summary>Details</summary>


```shell
sudo crontab -e
```
- Add this to the end:(example)
```shell
@reboot python3 /home/pi/MUSICAL_DOOR_BELL/main.py &
```
  - If you want to add log-file:(example)
```shell
  @reboot sudo /usr/bin/python3 /home/pi/MUSICAL_DOOR_BELL/main.py > /home/pi/MUSICAL_DOOR_BELL/logfile.log 2>&1 &
```

</details>

#### **<ins>Better way to run on startup script:</ins>**
 <details>
 <summary>Details</summary>


```shell
sudo nano /etc/rc.local
```
- If you want delay
```shell
sleep 30
```
- Add this to the end:(example)
```shell
su -c "python3 /path/to/your/script.py > /path/to/your/logfile.log 2>&1" pi &
```
- Update permission:
```shell
sudo chmod +x /etc/rc.local
```
</details>

#### **<ins>Run app with UI in startup use this:</ins>**
 <details>
 <summary>Details</summary>


```shell
sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
```
- Add this in the end:(example)
```shell
@/usr/bin/python /home/pi/example.py
```
</details>

#### **<ins>Hide the taskbar command this line:</ins>**
 <details>
 <summary>Details</summary>


```shell
sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
```
- Command this line:
```shell
#@lxpanel --profile LXDE-pi
```
</details>

#### **<ins>Chnage splash screen:</ins>**
 <details>
 <summary>Details</summary>


- first change the splash image in what you like in this dir:
  - /usr/share/plymouth/themes/pix
  - then run this command:
```shell
sudo plymouth-set-default-theme --rebuild-initrd pix
```
- Disable rainbow splash:
	- Add or edit this line:
```shell
disable_splash=1 to /boot/config.txt
```
- To remove the blinking curse add this:
```shell
vt.global_cursor_default=0 
```
- To:
```shell
/boot/cmdline.txt
```
- Mute kernel logs (only show critical errors) Add:
```shell
loglevel=3
```
- To:
```shell
/boot/cmdline.txt 
```
</details>

#### **<ins>Run GUI script from SSH:</ins>**
 <details>
 <summary>Details</summary>


- Run this command:
```shell
export DISPLAY=:0
```
- Now you can run the script
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
