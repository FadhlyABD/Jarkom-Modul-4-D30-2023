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


## Variable Length Subnet Masking (VLSM)
Pada sesi ini kita akan membuat topologi kita pada Cisco Packet Tracer (CPT). Setelah membuat topologi, yang pertama kita lakukan selanjutnya adalah melakukan perhitungan untuk subnetting. Berikut langkah-langkahnya.

### Subnetting
- Lakukan pembagian untuk jumlah subnet yang ada pada topologi yang telah dibuat dan akan didapatkan pembagiannya sebagai berikut.
![Alt text](Images/subnet.png)
- Lakukan perhitungan terhadap jumah IP pada tiap-tiap subnet yang telah dibagi.
![Alt text](Images/rute.jpg)
- Buat sebuah tree yang merepresentasikan pembagian ip dengan metode VLSM dari tiap-tiap subnet sebagaimana berikut.
![Alt text](Images/vlsmtree.png)

**Penjelasan:**
- Pada pembagian subnet tercatat total ip adalah 4255 dan netmask yang cukup menampungnya adalah `/19` (menampung 8190 ip).
- Sehingga root dari tree memiliki netmask `/19` dengan ip yang dimulai dari `192.206.0.0`.
- Left child dari tree akan selalu menunjukkan awal mula dari ip yang tersedia, sedangkan right child adalah ip setelah ip left child.
- Iterasi dilakukan terus menerus mulai dari netmask `/19` hingga `/30`.
- Sehingga pada akhirnya diperoleh pembagian IP dari tree VLSM tersebut sebagai berikut.
![Alt text](Images/ipvlsm.jpg)
