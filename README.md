  

#ovmf from - https://github.com/kholia/OSX-KVM/tree/master  
#run qemu both uefi and accel  
qemu-system-x86_64 -m 2512 \
-drive if=pflash,format=raw,readonly=on,file=OVMF_CODE.fd  \
-drive if=pflash,format=raw,readonly=on,file=OVMF_VARS.fd \
-accel hvf \
-drive file=steamdeck-repair-20231127.10-3.5.7.img,format=raw 

#block external selenium access  
iptables -A INPUT -p tcp --destination-port 4444 -j DROP

#resize ext4  
growpart  /dev/sda 1
(maybe reboot)
resize2fs /dev/sda1


#fix apache permission error  
mount --bind -o uid=1,gid=1 /root/mounts/mac11/Volumes/4TB/html /var/www/html

#android change package id command line  
LC_CTYPE=C && LANG=C && grep -ril . -e com.example.app --exclude-dir=.git | xargs sed -i '' -e 's/com.example.app/com.rulyua.memory_game/g'

#resize images macos  
mkdir -p resized && sips -Z 640 *.jpg --out resized/




#setup virtual host postfix (alpine linux)  
##/etc/postfix/main.cf
home_mailbox = /home/vmail/%d/%n/Maildir
virtual_mailbox_domains = top-mp3.org, virtual.host
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = lmdb:/etc/postfix/virtual-mailbox
virtual_uid_maps = static:2000
virtual_gid_maps = static:2000

##/etc/postfix/virtual-mailbox  
root@top-mp3.org   top-mp3.org/root/Maildir/

#and look at tail -f /var/log/messages  
