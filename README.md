# linux-commands
## Raspberry pi: 

 - **<u>Globale install for opencv:</u>**
	- sudo apt install python3-opencv

- **venv opencv install opencv:**
	- pip install --upgrade pip
	- pip install opencv-python
	- pip install opencv-python --verbose (to track the process)
	
- **<u>open audio sound:</u>**
	- alsamixer

- **<u>Copy folder from pi to pc:</u>**
	- scp -r pi@192.168.68.150:~/MUSICAL_DOOR_BELL /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR 

- **<u>Copy file from pi to pc:</u>**
	- scp pi@192.168.68.150:~/MUSICAL_DOOR_BELL/main.py /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR

- **<u>Add you script at startup:</u>**
	- sudo crontab -e
		- @reboot python3 /home/pi/MUSICAL_DOOR_BELL/main.py &
	- If you want to add logfile:
		- @reboot sudo /usr/bin/python3 /home/pi/MUSICAL_DOOR_BELL/main.py > /home/pi/MUSICAL_DOOR_BELL/logfile.log 2>&1 &
	- Better way to run on startup script:
		- sudo nano /etc/rc.local
		- If you want delay
			- sleep 30
		- su -c "python3 /path/to/your/script.py > /path/to/your/logfile.log 2>&1" pi &
		- sudo chmod +x /etc/rc.local

- **<u>Run app with UI in startup use this:</u>**
	- sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	- Add this in the end:
		-  @/usr/bin/python /home/pi/example.py

- **<u>Hide the taskbar command this line:</u>** 
	-  sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	-  #@lxpanel --profile LXDE-pi  (command this line)

- **<u>Chnage splash screen:</u>**
	-  first change the splash image in what you like in this dir:
	-  /usr/share/plymouth/themes/pix
	-  then run this command:
		-  sudo plymouth-set-default-theme --rebuild-initrd pix
	- Disable rainbow splash:
		- Add or edit this line:
			-  disable_splash=1 to /boot/config.txt
	- To remove the blinking curser add this:
		- vt.global_cursor_default=0 to /boot/cmdline.txt
	- Mute kernel logs (only show critical errors): 
		- Add loglevel=3 to the /boot/cmdline.txt