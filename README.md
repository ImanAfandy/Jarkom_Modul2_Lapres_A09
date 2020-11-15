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
