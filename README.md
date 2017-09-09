# Install Apache And Maria DB On Raspberry Pi 3

## Step 1

1. Download CentOs Userland 7 Minimal at http://mirror.centos.org/altarch/7/isos/armhfp/CentOS-Userland-7-armv7hl-Minimal-1611-RaspberryPi3.img.xz
2. Format Micro SD
2. Extract file
3. Download Rufus at http://filehippo.com/download_rufus/
4. Install Rufus
5. Run Rufus and put CentOs image file to Micro SD
6. Put Micro SD to Raspberry Pi 3
7. Run Raspberry Pi 3 with monitor and keyboard
8. Run commands below

## Command

/usr/local/bin/rootfs-expand

firewall-cmd --permanent --add-port=800/tcp

firewall-cmd --permanent --add-port=80/tcp

yum update -y

yum install -y httpd

yum install -y mariadb-server mariadb

yum install -y php php-gd php-gd php-exif php-libxml php-mbstring php-mysql

yum install -y sysstat

yum install -y unzip 

systemctl start httpd.service

systemctl enable httpd.service

systemctl start mariadb.service

systemctl enable mariadb.service

cd /var/www

chown -R apache html

chmod -R 755 html

## Setup Database

After install Apache and Maria DB, you must set root password for Maria DB.

mysql -u root

Execute query to set root password

SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yournewpassword');

SET PASSWORD FOR 'root'@'%' = PASSWORD('yournewpassword');



