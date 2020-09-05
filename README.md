#### sshfs debian
    sudo apt install sshfs
    mkdir local-folder/
    sshfs -o follow_symlinks user@remote.com:/home/user/ local-folder/
    sudo umount local-folder/


