# EndeavourOS
Just a compilation of various tweaks for my Alienware Aurora Ryzen Edition

# Mount second disk as a folder for Steam games
cd / && sudo mkdir GAMES  
sudo vi /etc/fstab  
/dev/sdx* /GAMES ext4 defaults,nofail 0 0  

# Add support for Xbox Series Controller
(It appears that you have to install for every kernel update)  
git clone https://github.com/atar-axis/xpadneo.git  
cd xpadneo  
sudo ./install.sh  

# Stop KDE indexing files
balooctl suspend  
balooctl disable  

# Firefox micro stuttering videos (KDE)
(Don't know what specific tweak solved this issue, so I write all tweaks done)  
about:config in Firefox  
gfx.webrender.all=true  
layers.acceleration.force-enabled=true  
sudo pacman -S ffmpeg openh264  

# Bluetooth isn't working under Gnome  
This is simple. Check if the service is enabled.  
systemctl status bluetooth  
systemctl start bluetooth  

# Ignore updates  
So I got an nvidia update that broke my OS and I did a downgrade to a functional version.  
In order to ignore updates I did:  
sudo vi /etc/pacman.conf  
```
`# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup
IgnorePkg   = nvidia-dkms nvidia nvidia-utils lib32-nvidia lib32-nvidia-utils op
encl-nvidia nvidia-settings lib32-opencl-nvidia
```
So if you do an update with sudo pacman -Syyu, it will print:
```
 -> lib32-nvidia-utils: ignoring package upgrade (515.65.01-1 => 515.76-1)
 -> lib32-opencl-nvidia: ignoring package upgrade (515.65.01-1 => 515.76-1)
 -> nvidia-dkms: ignoring package upgrade (515.65.01-2 => 515.76-1)
 -> nvidia-settings: ignoring package upgrade (515.65.01-1 => 515.76-1)
 -> nvidia-utils: ignoring package upgrade (515.65.01-2 => 515.76-1)
 -> opencl-nvidia: ignoring package upgrade (515.65.01-2 => 515.76-1)
```
