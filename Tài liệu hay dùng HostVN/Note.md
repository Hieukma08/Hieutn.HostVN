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
14. Lệnh kiểm tra file php.ini trong direcadmin 

- Kiểm tra dung lượng upload 
```
# php -i|grep upload_max
```
- Kiểm tra đường dẫn file 
```
# php -i|grep php.ini
```
*Note : khởi động lại hệ thống webserver*

15. Bản ghi mail outlook 
```
Truy cập vào link tắt kém an toàn https://myaccount.google.com/u/8/lesssecureapps?utm_source=google-account&utm_medium=web

pop.gmail.com

smtp.gmail.com
```
16. lệnh tìm mail đang cố đăng nhập và bị chặn ssh vào 
```
cat /var/log/maillog | grep IP

tail -10000 /var/log/maillog | grep kingbond.vn
```
17. Kiểm tra mail bị block 

```
vi /etc/cpanel_exim_system_filter
```
18. Clear the admin balacklist solus 
```
php /usr/local/solusvm/scripts/clearauthlog.php --system --clear=all
```
19. Khởi động lại service Kerio 
```
sudo service kerio-connect restart [program:queue] command=bash /usr/local/bin/send_queues.sh
```
20. Điều hướng http sang https .htaccess
```
RewriteCond %{HTTPS} !=on [NC]
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
```

21. check user domain 
```
/scripts/whoowns pharbaco.com.vn
```
22. Câu lệnh kiểm tra mail đang spam 
```
tail -n 1000000 /var/log/exim_mainlog | grep IP
```
23. enh add du lieu databases khi file qua 50mb
```
mysql -u root -p
b2: show databases ;
b3: use nhbocmlo_alibaba ;
b4: source /duong dan thu muc/tendatabases ;
```

24. Làm rỗng file dữ nguyên file nhưng xóa dữ liệu ở trong
```
cat /dev/null > tenfile 
```
25. mail queue kerio 
```
/opt/kerio/mailserver/store/queue  đây là đường dẫn 

rm -rf * -R đây là lệnh xóa tất cả các file trong thư mục để ý với lệnh này 
```

26. câu lệnh kiểm tra directadmin và root sql 
```
cat /usr/local/directadmin/scripts/setup.txt
```
27. 