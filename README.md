# LAB-38-SSTP
Kamis 21 Agustus 2025  

# SSTP (Secure Socket Tunneling Protocol)  
  SSTP merupakan sebuah PPP TUnnel dengan TLS 1.0 Channel. Fitur ini berjalan pada protokol TCP dan Port 443. Supaya dapat memanfaatkan SSTP secara optimal dengan keamanan yang baik, kita diharuskan menambahkan sertifikat SSL untuk koneksi antara server dan client. Kita bisa mendapatkan sertifikat SSL itu dengan membeli di vendor-vendor yang ada atau kita bisa membuat sertifikat sersebut mengunakan OpenSSL. Mikrotik juga sudah menambahkan fitur untuk membuat sertifikat SSL mulai dari RouterOS versi 6.xx dan bisa juga diterapkan ke perangkat non-Mikrotik.  
  
# Konfigurasi SSTP
  1. Lakukan dulu basic config sampai Mikrotik terkoneksi ke internet.
  ![](IMAGES/)  
  ![](IMAGES/)  
  ![](IMAGES/)  
  ![](IMAGES/)  
  2. Lalu masuk ke **PPP > Interface > SSTP server**, enable, lalu ubah Default profile nya ke **default-encryiption**, jika sudah APPLY lalu OK.  
  ![](IMAGES/)  
  3. Setelah itu, kita perlu membuat akun di secret **PPP > Secret > add**
  ![](IMAGES/)  
  4. Simple nya untuk konfigurasi SSTP server sampai sini sudah cukup.

# Konfigurasi SSTP part 2
  1. Sekarang kita buat sertifikat, di **system > certificate > add**, ada 3 sertifikat yang harus kita buat, untuk yang CA di bagian common name kita isi dengan IP Public router kita.  
  ![](IMAGES/)  
  2. Sekarang kita harus self sign in, di terminal karna di mikrotik belum ada GUI nya. Kita coba daftarkan dulu yang CA-Template.  
  ![](IMAGES/)  
  3. Jika sudah selesai, kita bisa lihat ada flag KLAT di GUI sertificate, K=Private Key, L=crl, A= Authority, T=Trusted. Setelah ini barulah kita bisa melakukan proses self sign in untuk server dan client kita.
  ![](IMAGES/)
  4. Sekarang buat agar client dan server dapat flag Trusted.
  ![](IMAGES/)
  5. Jika sudah, baru sekarang kita dapat mengunakannya di SSTP. Sekarang kita dapat export sertifikat untuk di import ke client. 
  ![](IMAGES/)  
  ![](IMAGES/)
  6. Sekarang pindahkan file ke windows dan import ke router B.
  ![](IMAGES/)
  ![](IMAGES/)  
  8. 
