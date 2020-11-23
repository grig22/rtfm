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

### static dynamic reinterpret_cast
https://stackoverflow.com/questions/332030/when-should-static-cast-dynamic-cast-const-cast-and-reinterpret-cast-be-used
https://stackoverflow.com/a/332086

`static_cast` is the first cast you should attempt to use. It does things like implicit conversions between types (such as `int` to `float`, or pointer to `void*`), and it can also call explicit conversion functions (or implicit ones).

`const_cast` can be used to remove or add `const` to a variable; no other C++ cast is capable of removing it (not even `reinterpret_cast`). `const_cast` also works similarly on `volatile`, though that's less common.

`dynamic_cast` is exclusively used for handling polymorphism. You can cast a pointer or reference to any polymorphic type to any other class type (a polymorphic type has at least one virtual function, declared or inherited).

`reinterpret_cast` is the most dangerous cast, and should be used very sparingly. It turns one type directly into another — such as casting the value from one pointer to another, or storing a pointer in an `int`, or all sorts of other nasty things.

C-style cast and function-style cast are casts using `(type)object` or `type(object)`, respectively, and are functionally equivalent.

### Tor Browser Transmission
https://askubuntu.com/questions/138089/where-is-tor-browser-opening-transmission-from-how-can-i-open-the-same-transm

Regular Transmission profile is stored in `$HOME/.config/transmission`  
Tor-browser Transmission profile is inside the tor-browser directory, e.g. `tor-browser_en-US/.config/transmission`

### Debian Disable suspend and hibernation
https://wiki.debian.org/Suspend#Disable_suspend_and_hibernation

For systems which should never attempt any type of suspension, these targets can be disabled at the systemd level with the following:
    sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
    
To re-enable hibernate and suspend use the following command:
    sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target
