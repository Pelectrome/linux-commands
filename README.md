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
🔹To track the process:
<pre><code class="language-shell"> pip install opencv-python --verbose 
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
 <summary><ins>Add you script at startup:</ins></summary>
<pre><code class="language-shell">sudo crontab -e
</code></pre> 
🔹Add this to the end:(example)
<pre><code class="language-shell">@reboot python3 /home/pi/MUSICAL_DOOR_BELL/main.py &
</code></pre> 
🔹If you want to add log-file:(example)
<pre><code class="language-shell">@reboot sudo /usr/bin/python3 /home/pi/MUSICAL_DOOR_BELL/main.py > /home/pi/MUSICAL_DOOR_BELL/logfile.log 2>&1 &
</code></pre> 
</details>
 <details>
 <summary><ins>Better way to run on startup script:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/rc.local
</code></pre> 
🔹If you want delay
<pre><code class="language-shell">sleep 30
</code></pre> 
🔹Add this to the end:(example)
<pre><code class="language-shell">su -c "python3 /path/to/your/script.py > /path/to/your/logfile.log 2>&1" pi &
</code></pre> 
🔹Update permission:
<pre><code class="language-shell">sudo chmod +x /etc/rc.local
</code></pre> 
</details>
 <details>
 <summary><ins>Run app with UI in startup use this:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
</code></pre> 
🔹Add this in the end:(example)
<pre><code class="language-shell">@/usr/bin/python /home/pi/example.py
</code></pre> 
</details>
 <details>
 <summary><ins>Hide the taskbar command this line:</ins></summary>
<pre><code class="language-shell">sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
</code></pre> 
🔹Command this line:
<pre><code class="language-shell">#@lxpanel --profile LXDE-pi
</code></pre> 
</details>
 <details>
 <summary><ins>Chnage splash screen:</ins></summary>
  <div>🔹first change the splash image in what you like in this dir:
	<ul>/usr/share/plymouth/themes/pix</ul>
</div>
🔹then run this command:
<pre><code class="language-shell">sudo plymouth-set-default-theme --rebuild-initrd pix
</code></pre> 
<div>🔹Disable rainbow splash:
	<ul>Add or edit this line:</ul>
</div>
<pre><code class="language-shell">disable_splash=1 to /boot/config.txt
</code></pre> 
🔹To remove the blinking curse add this:
<pre><code class="language-shell">vt.global_cursor_default=0 
</code></pre> 
🔹To:
<pre><code class="language-shell">/boot/cmdline.txt
</code></pre> 
🔹Mute kernel logs (only show critical errors) Add:
<pre><code class="language-shell">loglevel=3
</code></pre> 
🔹To:
<pre><code class="language-shell">/boot/cmdline.txt 
</code></pre> 
</details>
 <details>
 <summary><ins>Run GUI script from SSH:</ins></summary>
🔹  Run this command:
<pre><code class="language-shell">export DISPLAY=:0
</code></pre> 
🔹‎ Now you can run the script
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
