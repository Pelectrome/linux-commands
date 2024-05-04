# Linux-commands

## Raspberry pi:

1. **<ins>Globale install for opencv:</ins>**
```
sudo apt install python3-opencv
```

3. <ins>**venv opencv install opencv:**</ins>
```
pip install --upgrade pip
```
```
pip install opencv-python
```
- To track the process:
```
pip install opencv-python --verbose 
``` 

		
1. **<ins>open audio sound:</ins>**
```
alsamixer
```

2.  **<ins>Copy folder from pi to pc:</ins>**
```
scp -r pi@192.168.68.150:~/MUSICAL_DOOR_BELL /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR
```

4.  **<ins>Copy file from pi to pc:</ins>**
`scp pi@192.168.68.150:~/MUSICAL_DOOR_BELL/main.py /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR`

5. **<ins>Add you script at startup:</ins>**
	  - Run this command:
	    - sudo crontab -e
	  - Add this to the end:
	    - @reboot python3 /home/pi/MUSICAL_DOOR_BELL/main.py &
	  - If you want to add logfile:
	    - @reboot sudo /usr/bin/python3 /home/pi/MUSICAL_DOOR_BELL/main.py > /home/pi/MUSICAL_DOOR_BELL/logfile.log 2>&1 &
	  - Better way to run on startup script:
	    - sudo nano /etc/rc.local
	    - If you want delay
	      - sleep 30
	    - su -c "python3 /path/to/your/script.py > /path/to/your/logfile.log 2>&1" pi &
	    - sudo chmod +x /etc/rc.local

6. **<ins>Run app with UI in startup use this:</ins>**
	  - sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	  - Add this in the end:
	    - @/usr/bin/python /home/pi/example.py

7. **<ins>Hide the taskbar command this line:</ins>**
	  - sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	  - #@lxpanel --profile LXDE-pi (command this line)

8. **<ins>Chnage splash screen:</ins>**
	  - first change the splash image in what you like in this dir:
	  - /usr/share/plymouth/themes/pix
	  - then run this command:
	    - sudo plymouth-set-default-theme --rebuild-initrd pix
	  - Disable rainbow splash:
	    - Add or edit this line:
	      - disable_splash=1 to /boot/config.txt
	  - To remove the blinking curser add this:
	    - vt.global_cursor_default=0 to /boot/cmdline.txt
	  - Mute kernel logs (only show critical errors):
	    - Add loglevel=3 to the /boot/cmdline.txt
	    
10. **<ins>Run GUI script from SSH:</ins>**
	  - Run this command:
	    - export DISPLAY=:0
	  - Now you can run the script


## Linux:

 1. keyboard shortcuts  : 
	-  hibernate : sudo systemctl hibernate (Shift + Alt + H)
	-  new-window : nautilus --new-window (Super + E)
	-  reboot : sudo reboot now (Shit + Alt + R)
	-  shutdown : sudo shutdown now (Shit + Alt + S)
	-  open terminal : gnome-terminal (Ctrl + Alt + T)
	-  enable gnome extensions : gnome-extensions enable hanabi-extension@jeffshee.github.io (Ctrl + Alt + L)
	-  disable gnome extensions : gnome-extensions disable hanabi-extension@jeffshee.github.io (Ctrl + Alt + L)
	
2. Update Swap for hibernation.
   ```
   sudo nano /etc/fstab
    ```
 add this : UUID= < UUID >          none            swap    sw              0       0
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
