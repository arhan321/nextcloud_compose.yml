======== install nextcloud ======== 

compose yml : 

services:
  mysql_nextcloud:
    image: mariadb:10.2
    container_name: mysql_nextcloud
    restart: unless-stopped
    tty: true
    ports:
      - "33344:3306"
    volumes:
      - ./database/data:/var/lib/mysql
      - ./conf.d:/etc/mysql/conf.d:ro
    environment:
      MYSQL_ROOT_PASSWORD: Djony
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: jhonss
      MYSQL_PASSWORD: Djony
    read_only: false

  nextcloud_app:
    image: nextcloud:latest
    container_name: nextcloud_app
    restart: always
    ports:
      - 8080:80
    depends_on:
      - mysql_nextcloud
    volumes:
      - nextcloud_data:/var/www/html
    environment:
      MYSQL_PASSWORD: Djony
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: jhonss
      MYSQL_HOST: mysql_nextcloud
      
volumes:
  database:
  nextcloud_data:


setelah itu up jika saat pendaftaran pertama error silahakn masuk ke container MySQL nya, dan berikan querry izin user db nya : 

mysql -u root -p

contoh perintah nya jika nama user nya jhonss : 
CREATE DATABASE IF NOT EXISTS nextcloud;
GRANT ALL PRIVILEGES ON nextcloud.* TO 'jhonss'@'%' IDENTIFIED BY 'Djony';
FLUSH PRIVILEGES;
EXIT;

setelah itu pasti akan berhasil !!!!!!!!!

================ END install nextcloud ==============================
