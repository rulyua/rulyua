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
