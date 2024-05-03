# linux-commands
## Raspberry pi: 

 - **<ins>Globale install for opencv:</ins>**
	- sudo apt install python3-opencv

- **<ins>venv opencv install opencv:</ins>**
	- pip install --upgrade pip
	- pip install opencv-python
	- pip install opencv-python --verbose (to track the process)
	
- **<ins>open audio sound:</ins>**
	- alsamixer

- **<ins>Copy folder from pi to pc:</ins>**
	- scp -r pi@192.168.68.150:~/MUSICAL_DOOR_BELL /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR 

- **<ins>Copy file from pi to pc:</ins>**
	- scp pi@192.168.68.150:~/MUSICAL_DOOR_BELL/main.py /C:\Users\PC\Documents\Python\MUSICAL_DOOR_BELL_OUTDOOR

- **<ins>Add you script at startup:</ins>**
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

- **<ins>Run app with UI in startup use this:</ins>**
	- sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	- Add this in the end:
		-  @/usr/bin/python /home/pi/example.py

- **<ins>Hide the taskbar command this line:</ins>** 
	-  sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
	-  #@lxpanel --profile LXDE-pi  (command this line)

- **<ins>Chnage splash screen:</ins>**
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
- Run GUI script from SSH:
	- Run this command:
		- export DISPLAY=:0
	- Now you can run the script