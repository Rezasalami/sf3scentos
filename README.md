# sf3scentos
run s3sf in centos 7 

# install sf3s
sudo yum install s3fs-fuse
# add access key
echo ACCESS_KEY_ID:SECRET_ACCESS_KEY > ${HOME}/.passwd-s3fs
cat ${HOME}/.passwd-s3fs
chmod 600 ${HOME}/.passwd-s3fs
# add allow all user access to mount 
vim /etc/fuse.conf
# add it in fuse.conf
user_allow_other

# mount s3fs arvancloud
s3fs -o allow_other -o umask=0002 baketname [path] -o use_path_request_style -o url=https://*.arvanstorage.com -o passwd_file=~/.passwd-s3fs

# show mount storage
df -h 

# umount s3fs 
umount s3fs -f

#windows Task
"C:\Program Files\S3 Browser\s3browser-con.exe" sync arvanstorage.com X:\Backups s3:bakup ncdhs
