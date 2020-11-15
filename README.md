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
























