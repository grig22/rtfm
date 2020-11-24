### sshfs debian
    sudo apt install sshfs
    mkdir local-folder/
    sshfs -o follow_symlinks user@remote.com:/home/user/ local-folder/
    sudo umount local-folder/

### apache2 cgi python debian
    # cd /etc/apache2/
    # ln -rs mods-available/cgi.load mods-enabled/

    # nano /etc/apache2/apache2.conf
    <Directory /var/www/>
        Options Indexes FollowSymLinks
        Options +ExecCGI
        AddHandler cgi-script py
        AllowOverride All
        Require all granted
    </Directory>

    # systemctl restart apache2.service

    # nano /var/www/html/.htaccess
    DirectoryIndex index.py

    -rwxr-xr-x /var/www/html/index.py

    #!/usr/bin/python3
    print("Content-type: text/html\n\n")
    print("hello")

### Tor Browser Transmission
https://askubuntu.com/questions/138089/where-is-tor-browser-opening-transmission-from-how-can-i-open-the-same-transm

Regular Transmission profile is stored in `$HOME/.config/transmission`  
Tor-browser Transmission profile is inside the tor-browser directory, e.g. `tor-browser_en-US/.config/transmission`  
To create a common profile, you must create a symlink from one to the other using `ln -s`  
I recommend leaving the normal config ($HOME/.config) intact and linking the Tor config to it

### Debian Disable suspend and hibernation
https://wiki.debian.org/Suspend#Disable_suspend_and_hibernation

For systems which should never attempt any type of suspension, these targets can be disabled at the systemd level with the following:

    sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
    
To re-enable hibernate and suspend use the following command:

    sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target

### Gnome window borders
https://askubuntu.com/questions/976030/how-to-enable-add-window-borders-in-17-10-18-04  
1. Make a file ~/.config/gtk-3.0/gtk.css
2. Add the lines:
```
decoration {
  border: 1px solid gray;
  background: gray;
}
```
3. Reboot or log out + log in
