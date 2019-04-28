# ganti-document-root

Sebelum melakukan konfigurasi untuk merubah letak root folder web server apache tersebut, saya akan membuat folder baru yang
nantinya akan digunakan sebagai root folder web server apache. 

Lokasi sebelumnya:

 /var/www/html/


akan dipindah ke:

 /home/haffsriyandrayusuf/Dev 


Maka saya akan membuat folder terlebih dahulu di lokasi /website dengan menjalankan perintah:

 sudo mkdir /home/haffsriyandrayusuf/Dev


kemudian saya ubah permisinya agar dapat dibaca oleh pengakses web server (orang lain) dan dapat ditulisi oleh web server 
itu sendiri, dengan menjalankan perintah:

 sudo chmod 777 -R /home/haffsriyandrayusuf/Dev


untuk mengidentifikasi perubahan saya buat sebuah folder baru di dalam root folder /website dengan perintah:

 mkdir /home/haffsriyandrayusuf/Dev


kemudian saya buka file konfigurasi web server apache untuk melakukan perubahan letak lokasi root folder dengan menjalankan 
perintah:

 sudo vim /etc/apache2/sites-available/000-default.conf


kemudian cari bagian:

 DocumentRoot /home/haffsriyandrayusuf/Dev


kemudian ubah menjadi:

 #DocumentRoot /var/www/html
 DocumentRoot /home/haffsriyandrayusuf/Dev


simpan, kemudian buka juga file konfigurasi yang ada di /etc/apache2/apache2.conf dengan menjalankan perintah:

 sudo vim /etc/apache2/apache2.conf


lalu tambahkan konfigurasi di bawah:

 <Directory /home/haffsriyandrayusuf/Dev/>
   Options Indexes FollowSymlinks
   AllowOverride None
   Require all granted
 </Directory>


simpan, kemudian restart layanan web server apache dengan perintah:

 sudo service apache2 restart


silahkan akses kembali alamat ip web server apache anda (alamat ip web server saya 192.168.0.254) atau di http://localhost, 
maka root folder web server apache telah berpindah 
dari /var/www/html ke /home/haffsriyandrayusuf/Dev.
Selamat mencoba dan semoga membantu :-)
