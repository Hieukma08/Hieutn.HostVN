## Một số tài liệu hay dùng khi làm việc với mailserver và webserver 

1. Check tài nguyên sử dụng Linux 

```
df -h 
free -m 
lscpu
```
2. Cấu hình htaccess cho web laravel 

```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
RewriteCond %{HTTPS} !=on [NC]
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
</IfModule>

# END WordPress
```

```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress
```
Có hai mẫu htaccess 

3. Cấu hình swap 

```
wget https://raw.githubusercontent.com/domanhduy/ghichep/master/DuyDM/Swap-Script/nh-create-swap.sh
sh ./nh-create-swap.sh
```

4. Câu lệnh mở tất cả các tiến trình trên mail kerio-connect 

```
iptables -F service kerio-connect start service kerio-connect stop service kerio-connect restart
```
5. Cập nhật Letsencryp trên directadmin 

```
cd /usr/local/directadmin/custombuild
vi options.conf để xem có những phiên bản PHP nào .

./build update
./build letsencrypt

./build set php1_release 5.6
./build set php2_release 7.2
./build set php3_release 7.4
./build set php1_mode suphp
./build set php2_mode suphp
./build set php3_mode suphp
./build set mod_ruid2 no
./build update
./build php d
./build apache d
./build rewrite_confs
```
6. Kết nối FTP 

- Truy cập FTP qua FileZilla B1 : Mở phần mềm FTP Client FileZilla Ấn Ctrl + S hoặc File -> Site Manager (Link hình ảnh chi tiết : https://prnt.sc/qezagy ) B2 : Ở mục Encryption quý khách chọn : Only user plain FTP (insecure) (Link hình ảnh chi tiết : https://prnt.sc/qezbo6 )

7. lenh xoa du lieu trong file ma van giu nguyen ten file (auth.log la ten file )

```
cat /dev/null > auth.log
```
8. Lệnh cài đặt quét virus

```
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh

bash imav-deploy.sh
```
9. Kiểm tra ram có bị full 
```
tail -1000 /var/log/messages | grep memory
```
10.fix lỗi chỉnh qouta user directadmin 

```
cd /usr/sbin
mv setquota setquota.old
touch setquota
chmod 755 setquota
```

11.chuyển web giữa các user trong directadmin

```
cd /usr/local/directadmin/scripts
./move_domain.sh callme24h.vn [user cũ] [user mới]
```

12.reset ram hosting
```
vi wp-config.php
thêm dòng: define('DISABLE_WP_CRON', true);
killall -9 lsphp
```
13.kiểm tra ram có bị tạm ngưng

```
dmesg -T --level err

cd /var/log
tail -10000 messages | grep memory

dmesg messages | grep "out"
```
