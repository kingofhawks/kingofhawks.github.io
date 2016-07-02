Mount shared folders with VirtualBox to ubuntu host
1. Install dependency  
apt-get update
apt-get install dkms build-essential linux-headers-$(uname -r)
2. Get Guest Addons  
sudo apt-get install virtualbox-guest-additions-iso  
3. Mount Guest Addons   
mount /dev/cdrom /mnt  
4. Install Guest Addons  
<pre>
<code>
cd /mnt
./VBoxLinuxAdditions.run
</code>
</pre>
5. Add user to group 'vboxsf'
sudo usermod -a -G vboxsf username(or sudo adduser your-user vboxsf)
6. Reboot VM


## References
https://www.turnkeylinux.org/docs/virtualbox-guest-addons
https://help.ubuntu.com/community/VirtualBox/GuestAdditions
https://www.virtualbox.org/manual/ch04.html#idm1967
http://stackoverflow.com/questions/28328775/virtualbox-mount-vboxsf-mounting-failed-with-the-error-no-such-device