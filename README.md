======== install nextcloud ======== 

compose yml : (mengikuti seperti yang di github)

setelah itu up jika saat pendaftaran pertama error silahakn masuk ke container MySQL nya, dan berikan querry izin user db nya : 

mysql -u root -p

contoh perintah nya jika nama user nya jhonss : 
CREATE DATABASE IF NOT EXISTS nextcloud;

GRANT ALL PRIVILEGES ON nextcloud.* TO 'jhonss'@'%' IDENTIFIED BY 'Djony';

FLUSH PRIVILEGES;

EXIT;

setelah itu pasti akan berhasil !!!!!!!!!

================ END install nextcloud ==============================
