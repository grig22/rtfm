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

