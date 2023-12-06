# Jarkom-Modul-4-D30-2023

## Group Member    :
| Nama                              | NRP        |
|-----------------------------------|------------|
|Abdullah Yasykur Bifadhlil Midror  |5025211035  |
|Muhammad Ahyun Irsyada             |5025211251  |

Berikut adalah demo laporan untuk praktikum modul 4

## Topologi
Topologi yang digunakan untuk praktikum modul 4 adalah sebagai berikut.
| <p align="center"> Topologi </p> |
| -------------------------------------------- |
| <img src="https://github.com/FadhlyABD/Jarkom-Modul-4-D30-2023/blob/main/Images/topologi.png" width = "400"/> |

## Subnet
![Alt text](Images/netmask.png)


## Variable Length Subnet Masking (VLSM)
Pada sesi ini kita akan membuat topologi kita pada Cisco Packet Tracer (CPT). Setelah membuat topologi, yang pertama kita lakukan selanjutnya adalah melakukan perhitungan untuk subnetting. Berikut langkah-langkahnya.

### Subnetting
- Lakukan pembagian untuk jumlah subnet yang ada pada topologi yang telah dibuat dan akan didapatkan pembagiannya sebagai berikut.
![Alt text](Images/subnet.png)
- Lakukan perhitungan terhadap jumah IP pada tiap-tiap subnet yang telah dibagi.
![Alt text](Images/rute.jpg)
- Buat sebuah tree yang merepresentasikan pembagian IP dengan metode VLSM dari tiap-tiap subnet sebagaimana berikut.
![Alt text](Images/vlsmtree.png)

**Penjelasan:**
- Pada pembagian subnet tercatat total IP adalah 4255 dan netmask yang cukup menampungnya adalah `/19` (menampung 8190 IP).
- Sehingga root dari tree memiliki netmask `/19` dengan IP yang dimulai dari `192.206.0.0`.
- Left child dari tree akan selalu menunjukkan awal mula dari ip yang tersedia, sedangkan right child adalah IP setelah IO left child.
- Iterasi dilakukan terus menerus mulai dari netmask `/19` hingga `/30`.
- Sehingga pada akhirnya diperoleh pembagian IP dari tree VLSM tersebut sebagai berikut.
![Alt text](Images/ipvlsm.jpg)

- Langkah selanjutnya adalah melakukan config pada tiap node di CPT berdasarkan IP dan subnet yang telah didapatkan sebelumnya
- Untuk isi config pembagian IP akan diset seperti ini:
  * Router memliki `IP NID + 1`
  * Host / Client memiliki `IP Rourter + 1` atau `IP Client sesubnet + 1`
  * Host / Client memiliki gateway sesuai IP router dalam subnet mereka
  * 1 router bisa memiliki beberapa IP karena dalam 1 router dapat menangani beberapa ethernet interface / subnet
- Berikut adalah contoh, jika sudah selesai melakukan config maka akan muncul konfigurasi ketika node dihover.
  1. Aura (Router)
     ![Alt text](Images/auracpt.png)
  2. Frieren (Router)
     ![Alt text](Images/frierencpt.png)
  3. Flamme (Router)
     ![Alt text](Images/flammecpt.png)
  4. Eisen (Router)
     ![Alt text](Images/eisencpt.png)
  5. GranzChannel (Client)
     ![Alt text](Images/granzcpt.png)
- Begitu juga untuk node yang lain menyocokkan dengan pembagian IP yang sudah dibagi sebelumnya.

### Routing
- Routing dilakukan dengan cara static dimana next hop dari routing adalah adjacent router terdekat dengan subnet yang ingin dituju.
- Semisal Aura ingin berkenalan dengan subnet A1 maka NID dan netmask diisi milik A1 dan next-hop nya adalah Frieren.
- Lakukan binding everywhere (0.0.0.0) pada router sesuai dengan yang ditandai dengan panah pada gambar dibawah ini.
  ![Alt text](Images/conowntopo.png)
- Kemudian untuk setiap router yang terhubung dengan router lain (next hop untuk berkenalan lebih dari 1 hop) yang memiliki host/client perlu mengenali subnet mereka juga.
- Contoh:
  - Flamme harus berkenalan dengan subnet A1 dan A14 <br>
  - Frieren harus berkenalan dengan subnet A1, A4, A5, A9, A14<br>
  - Aura harus berkenalan dengan semua subnet kecuali subnet A7, A8, A11<br>
- Binding everywhere dari setiap router cukup 1 saja yang mengarah ke router Aura / terdekat dengan Aura, hal ini dilakukan untuk efisiensi routing.
- Jika aura sudah disetup sebagaimana pengaturan routing di atas maka otomatis semua subnet bisa saling mengenal via Aura.
- Berikut adalah config lengkap dari masing router.
  - Frieren<br>
    ![Alt text](Images/rutefrieren.png)
  - Flamme<br>
    ![Alt text](Images/ruteflamme.png)
  - Fern<br>
    ![Alt text](Images/rutefern.png)
  - Himmel<br>
    ![Alt text](Images/rutehimmel.png)
  - Denken<br>
    ![Alt text](Images/rutedenken.png)
  - Eisen<br>
    ![Alt text](Images/ruteeisen.png)
  - Lugner<br>
    ![Alt text](Images/rutelugner.png)
  - Linie<br>
    ![Alt text](Images/rutelinie.png)
  - Lawine<br>
    ![Alt text](Images/rutelawine.png)
  - Heiter<br>
    ![Alt text](Images/ruteheiter.png)

### Testing
- Berikut adalah beberap bukti dari hasil ping antar node.<br>
  ![Alt text](Images/outputroute.png)


## CIDR (Classless Inter Domain Routing)
CIDR, atau Classless Inter-Domain Routing, adalah sebuah metode pengalamatan IP dan pengelompokan alamat IP untuk menggantikan sistem pengalamatan IP tradisional yang disebut sebagai kelas (Classful Network). CIDR diperkenalkan untuk mengatasi masalah pemborosan alamat IP yang terjadi dalam sistem kelas.

## Topologi untuk GNS3 
pada sesi CIDR topologi yang di gunakan adalah topologi menggunakn GNS3 yaitu : 
![Alt text](Images/topocidr.png)

Grouping Subnet : 

![Alt text](Images/topocidr2.jpg)

## Subnetting 
- Pertama tama kita gambar bagian bagian jumlah subnet yang ada pada topologi yang telah dibuat dan akan didapatkan pembagiannya sebagai berikut.
(poto)
- Lakukan perhitungan terhadap jumah IP pada tiap-tiap subnet yang telah dibagi.
	Penggabungan tingkat 1

	![Alt text](Images/cidr1.png)

	Penggabungan tingkat 2

	![Alt text](Images/cidr2.png)

	Penggabungan tingkat 3

  	![Alt text](Images/cidr3.png)
  
  	Penggabungan tingkat 4

  	![Alt text](Images/cidr4.png)
  
  	Penggabungan tingkat 5
  
  	![Alt text](Images/cidr5.png)
  
  	Penggabungan tingkat 6
  
  	![Alt text](Images/cidr6.png)
  
- Buat sebuah tree yang merepresentasikan pembagian ip dengan metode VLSM dari tiap-tiap subnet sebagaimana berikut.
  
	![Alt text](Images/hcidr.png)

*Penjelasan*
- Pada topologi Untuk melakukan perhitungan pada CIDR kita harus membagi bagi subnet mulai dari subnet yang paling bawah. Paling bawah berarti subnet yang paling jauh dari internet (gambar awan). Maka pada topologi yang digunakan, subnet yang dapat digabungkan adalah A1 dengan A2 dan subnet A7 dengan A8. Subnet yang digabung tersebut akan membentuk sebuah subnet lebih besar dari subnet-subnet kecil yang ada di dalamnya.  
- Pada setiap bagian subnet memiliki netmask yaitu host dalam bagian subnet yang memiliki netmask yang lebih besar di naikan satu tingkat lebih besar, contoh pada Subnet `B1` yang mana terdiri dari subnet `A1` dan `A5` yang mana memiliki netmask masing masing yaitu `/21` dan `/30`, dikarenakan subnet yang yang terbesar adalah `A1` dengan netmask `/21` maka netmask nya `B1` adalah `/20`
- Perbedaan antara pohon VLSM dengan pohon CIDR adalah ketika satu subnet diturunkan, netmask yang akan terbentuk disesuaikan dengan penggabungan subnet yang telah dilakukan sebelumnya.
- Iterasi dilakukan terus menerus mulai dari netmask `/16` hingga `/30`
- Sehingga pada akhirnya diperoleh pembagian IP dari tree VLSM tersebut sebagai berikut.
![Alt text](Images/cidrper.png)
