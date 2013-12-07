##Vsftpd config for raspberry pi

>This is what i did to mike my Raspberry Pi have FTP access for all of its users

#Install

        sudo apt-get install vsftpd
        
#Configure

*edit /etc/vsftpd.conf*

    anonymous_enable=NO
    chroot_local_user=NO
    chroot_list_enable=YES
    chroot_list_file=/etc/vsftpd.chroot_list
    
*edit /etc/vsftpd.chroot_list*

>First we have to make the file before we can edit it

    touch /etc/vsftpd.chroot_list

>now we can edit the file and put each user you would like to have access to into single line.

>*user1* *user2* *user3*

#Restart the service

    sudo service vsftpd restart
    

