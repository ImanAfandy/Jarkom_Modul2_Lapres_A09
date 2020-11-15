# Jarkom_Modul2_Lapres_A09

### Kelompok A04:
- Iman Afandy (05111740000129)
- Nodas Uziel Putra Serpara (5111840007007)


## Langkah pengerjaan : 
a. Membuat topologi 

b. Bash topologi yang sudah dibuat

c. Login ke semua UML 

d. Hilangkan tanda pagar (#) bagian net.ipv4.ip_forward=1 dengan perintah nano /etc/sysctl.conf pada router Surabaya.

e. Jalankan perintah sysctl -p

f. Setting IP dari setiap UML dengan dengan perintah nano /etc/network/interfaces.

g. ketikkan perintah service networking restart di setiap uml setelah setting ip.

h. ketikkan perintah atau membuat file script yang berisi iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE –s 192.168.0.0/16.

i. Export proxy pada setiap UML dengan sintaks seperti di bawah ini:

#### export http_proxy=”http://ITS-564415-ab673:798d2@proxy.its.ac.id:8080”
#### export https_proxy=”http://ITS-564415-ab673:798d2@proxy.its.ac.id:8080”
#### export ftp_proxy=”http://ITS-564415-ab673:798d2@proxy.its.ac.id:8080”


j. setelah itu lakukan perintah apt-get update.

## 1. untuk membuat sebuah website utama dengan alamat http://semeruyyy.pw

a) Buka MALANG dan update package lists dengan menjalankan command: apt-get update

b) Setelah melakukan update install bind9 pada MALANG dengan apt-get install bind9 -y

c) tambahkan zone pada /etc/bind/named.conf.local

![1](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/1_buatzone.png)

d) copykan file db.local pada path /etc/bind ke dalam folder semerua09.pw yang baru saja dibuat 
![2](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/1_cpdblokal.png)

e) Tambah server malang di conv.resolv Gresik
![3](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/1_tambahservermalang.png)

f) Coba ping di gresik 
![4](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/1_pinggresik.png)


#### 2. memiliki alias http://www.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO

a) Tambahkan www di /etc/bind/jarkom/semerua09.pw
![5](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/2_nambahwww.png)

b) Coba ping di gresik 
![6](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/2_pinggresik.png)

#### 3. buat subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO

a) Tambahkan subdomain penanjakan di file semerua09.pw di Malang 
![7](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/3_tambahsubpenanjakan.png)

b) Coba ping dari gresik
![8](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/3_pinggresik.png)


#### 4. buat reverse domain untuk domain utama

a) Tambahkan zone 73 di conf.local Malang 

![9](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/4_tambahzone73.png)

b) copy db.local ke file 73, lalu edit 
![10](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/4_cpdblokal.png)

c) Cek host IP Probolinggo 
![11](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/4_cekhost.png)


#### 5. buat DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website

a) 	Buat zone semeru di conf local mojokerto
![12](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/5_buatzone.png)

b) Coba ping di gresik 
![13](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/5_pinggresik.png)

#### 6. buat subdomain dengan alamathttp://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IPServer PROBOLINGGO

a) Edit  /etc/bind/jarkom/semerua09.pw

![14](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/6_edit.png)

b) <pr>nano /etc/bind/named.conf.options
comment dnssec-validation auto;
Tambahin allow-query{any;}; </pr>

![15](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/6_tambahkanalow.png)

c) edit /etc/bind/named.conf.local
![16](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/6_nanoconflocal.png)

d) ping di gresik 
![17](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/6_ping.png)



#### 7. buat subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO

a) edit semerua09.pw di probolinggo 
![18](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/7_edit.png)

b) Coba ping di gresik 
![19](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/7.png)

#### 8. Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw. Awalnya web dapat diakses menggunakan alamat http://semeruyyy.pw/index.php/home.

a)  Install apache di probolinggo (apt-get install apache2)

b)  Install php di probolinggo (apt-get install php5)

c)  Pindah ke directory /etc/apache2/sites-available

d)  Copy file default menjadi file semerua09.pw

e)  buka file dan Tambahkan servername dan serveralias 

![20](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/8_servername.png)

f) Buka http://semerua09.pw/index.php/home

![21](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/8.png)

#### 9. aktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home


a) Menjalankan perintah a2enmod rewrite untuk mengaktifkan module rewrite.

b) Restart apache dengan perintah service apache2 restart

c) buat file .htaccess di semerua09.pw 


![22](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/9_htaccess.png)

d) Buka http://semeruyyy.pw/home

![23](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/9.png)


#### 10. Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut:

/var/www/penanjakan.semeruyyy.pw

/public/javascripts
/public/css
/public/images
/errors

a) Buat directory website

b) Pindah ke direktori /etc/apache2/sites-available dan copy file default

c) Edit file semerua09.pw

![24](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/10_editfilepenanjakan.png)

d) Aktifkan konfigurasi (a2ensite)

e) Download file pendukung dengan wget

f) Buka penanjakan.semerua09.pw 

![25](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/10.png)

#### 11. Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.

a) tambahkan file /etc/apache2/sites-available/penanjakan.semerua09.pw


![26](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/11_editpenanjakan.png)

b) buka penanjakan.semerua09.pw/public/css

![27](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/11.png)


#### 12. Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.

a) Buat file penanjakan.semerua09.pw/.htaccess di Probolinggo

![28](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/12_htaccess.png)

b) Buka penanjakan.semerua09.pw/public/bebas 

![29](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/12.png)

#### 13. Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.

a) Menjalankan perintah a2enmod rewrite untuk mengaktifkan module rewrite.

b) Restart apache dengan perintah service apache2 restart

c) edit file konfigurasi yang berada di folder /etc/apache2/sites-available 


![30](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/13_penanjakan.png)

d) Restart apache dengan perintah service apache2 restart

e) Buka penanjakan/semerua09.pw/js

![31](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/13.png)


#### 14. sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw.

a) ganti port menjadi 8888 di naik.gunung.semerua09.pw 


![32](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/14_8888.png)

b) Tambahkan listen 8888

![33](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/14_listen888.png)


c) Buka naik.gunung.semerua09.pw:8888

![34](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/14_hasil.png)

#### 15. membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”.


a) edit naik.gunung.semerua09.pw

![35](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/15_editnaikgunung.png)

b)  Buka naik.gunung.semerua09.pw:8888


![36](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/15_hasil.png)

#### 16. Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw.

a) edit file default di probolinggo

![37](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/16_ubahdefault.png)

b) Buka ip probolinggo di browser


![38](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/16_hasil.png)


#### 17. Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

a) edit file penanjakan.semerua09.pw/.htaccess

![39](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/17_htaccess.png)

b) Buka penanjakan.semerua09.pw/public/images/


![40](https://raw.githubusercontent.com/ImanAfandy/Jarkom_Modul2_Lapres_A09/main/Gambar/17_hasil.png)














