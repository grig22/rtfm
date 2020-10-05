#### sshfs debian
    sudo apt install sshfs
    mkdir local-folder/
    sshfs -o follow_symlinks user@remote.com:/home/user/ local-folder/
    sudo umount local-folder/

#### apache2 cgi python debian
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

#### static dynamic reinterpret_cast
https://stackoverflow.com/questions/332030/when-should-static-cast-dynamic-cast-const-cast-and-reinterpret-cast-be-used
    static_cast is the first cast you should attempt to use. It does things like implicit conversions between types (such as int to float, or pointer to void*), and it can also call explicit conversion functions (or implicit ones).  
    const_cast can be used to remove or add const to a variable; no other C++ cast is capable of removing it (not even reinterpret_cast).  
    dynamic_cast is exclusively used for handling polymorphism. You can cast a pointer or reference to any polymorphic type to any other class type (a polymorphic type has at least one virtual function, declared or inherited).  
    reinterpret_cast is the most dangerous cast, and should be used very sparingly. It turns one type directly into another — such as casting the value from one pointer to another, or storing a pointer in an int, or all sorts of other nasty things.  
    C-style cast and function-style cast are casts using (type)object or type(object), respectively, and are functionally equivalent.
