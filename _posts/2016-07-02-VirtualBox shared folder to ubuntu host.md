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

When build node.js with npm, it will fail to create symlink in VB's shared folders on Windows 10 host.You could run from cmd on host as  
VBoxManage setextradata ubuntu16 VBoxInternal2/SharedFoldersEnableSymlinksCreate/sentry 1
VBoxManage getextradata ubuntu16 enumerate
And start VB as administrator.


## References
https://www.turnkeylinux.org/docs/virtualbox-guest-addons
https://help.ubuntu.com/community/VirtualBox/GuestAdditions
https://www.virtualbox.org/manual/ch04.html#idm1967
http://stackoverflow.com/questions/28328775/virtualbox-mount-vboxsf-mounting-failed-with-the-error-no-such-device
http://www.ahtik.com/blog/fixing-your-virtualbox-shared-folder-symlink-error/