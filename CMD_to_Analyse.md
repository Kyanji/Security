+ sudo -l
+ grep -r "/home/user/file" /etc/
+ find / -user root -perm -4000 -exec ls -ldb {} \;
