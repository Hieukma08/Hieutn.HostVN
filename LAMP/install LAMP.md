## Các bước cài đặt wordpress trên LAMP 
###  Bước 1 : Update và cài đặt các gói cơ bản 
1. Chuẩn bị 1 hệ điều hành ở đây là Ubuntu 20.04 

2. Cài đặt Apache 

- Cài đặt Apache 
```
sudo apt -y update

sudo apt -y install apache2

```
- Kiểm tra phiên bản Apache 

`apache -v`

- Khởi động dịch vụ và bật khởi chạy cùng hệ thống 

`systemctl restart`

`systemctl enable apache2`

*Note: Kiểm tra xem có bị chặn bởi tường lửa hay không nếu có thì cần allow tường lửa*

3. Cài đặt database ` Ở đây dùng mariaDB`

- Cài đặt 

`apt install -y software-properties-common mariadb-server mariadb-client `

- Kiểm tra dịch vụ : 

`systemctl status mariadb`

- Thiết lập thông tin tài khoản root DB : 

`mysql_secure_installation`

*Note : Tại đây chúng ta thiết lập 1 số thay đổi đối với mật khẩu root của DB, Tiếp đó hệ thống hỏi 1 số câu hỏi xác nhận thì chúng ta chỉ cần chọn Yes hết để thực hiện thay đổi* 

- Cài đặt và tạo cơ sở dữ liệu :

    - Truy cập vào cơ sở dữ liệu : 

    `mysql`
    - Tạo DB : 

    `create database wordpress; `

    - Tạo user và password 

    `create user 'wordpressuser'@'localhost' identified by 'password';`

    `GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;`

    - tải lại bảng các đặc quyền và thoát ra 
    `FLUSH PRIVILEGES;`

    `exit`


4. Cài đặt PHP 
*Ở đây cài đặt php phiên bản 7.4*

- Cài đặt : 
`apt -y install php libapache2-mod-php php-cli php-fpm php-json php-pdo php-mysql php-zip php-gd  php-mbstring php-curl php-xml php-pear php-bcmath`

- Kích hoạt cho php 7.4 
`a2enmod php7.4`

- Khởi động lại Apache
`systemctl reload apache2 `
*Note : sau khi kiểm tra lại hệ thống chúng ta thực hiện cài wp làm mã nguồn cho Apache*


5. Cài đặt wordpress : 
- Dowload mã nguồn của Wordpress về thư mục html của apache 
`wget https://wordpress.org/wordpress-5.9.3.zip`

- Giải nén file : 
`unzip wordpress-5.9.3.zip`

- Di chuyển các file trong file giải nén ra thư mục html 

- Chỉnh sửa file cấu hình wp-config.php 

6. Truy cập vào web site và tiến hành cài đặt Wordpress 




