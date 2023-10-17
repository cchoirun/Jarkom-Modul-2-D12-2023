# LAPRES2-JARKOM

|Nama |NRP|
|-----|---|
|Muhammad Revel Wivanto|5015211233|
|Muhammad Choirun Ni'am|5025221203|

## 1. Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni.
![Picture1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/449ed7d9-0aed-425b-b1fa-061bbe053dc8)

Sesuai dengan pembagian yang diberikan, maka kami kelompok D12 mendapatkan topologi no.1 yang dapat dilihat pada gambar. Kemudian untuk dapat mengakses internet maka kita perlu assign IP Address masing-masing switch pada router, sesuai yang ditunjukkan pada gambar.

<img width="593" alt="1 1" src="https://github.com/revelwivanto/Jarkom-Modul-1-D12-2023/assets/115228631/ba2d8e7b-9a74-4ec3-b7f9-2b18b33ba852">

Kita perlu mengkonfigurasikan 3 ethernet sesuai dengan jumlah switch yang ada. Kemudian secara urut kita assign IP Address mulai dari Yudhistira dengan IP 192.197.1.2, kemudian Nakula dengan IP 192.197.1.3. Dengan pola yang sama maka Werkudara dengan IP 192.197.2.2 dan Wisanggeni dengan IP 192.197.3.5

## 2. Buatlah website utama pada node arjuna dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok.
Untuk pembuatan domain utama, maka pada node arjuna kita jalankan perintah berikut
`nano \etc\bind\named.conf.local`
Kemudian kita edit sesuai dengan nama domain yang kita inginkan seperti pada gambar dibawah ini
![Picture2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/9a658541-108e-48a8-8753-52016fbd0c28)

Kemudian kita jalankan `nano \etc\bind\arjuna\arjuna.d12.com` dan ubah sesuai dengan nama domain yang diinginkan
![2 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/55ab668b-4a1a-48dc-ab40-1ef137cf58aa)

Kemudian kita test untuk mengetahui apakah ketika kita mengakses www.arjuna.d12.com akan mengarah ke arjuna.d12.com
![2 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/e33145a1-9f90-4a41-a1fd-805f710816fd)



## 3. Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com.
Langkah yang dilakukan mirip dengan nomor 2, kita jalankan perintah `nano \etc\bind\abimanyu\abimanyu.d12.com`

![3 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/74fcc81d-5a78-46f6-8646-1d80e59ebb57)

![3 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/dc63cf35-9985-4aac-b6c0-4b0a261baa1d)

## 4. Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.
untuk soal nomor 4 maka kita perlu mengatur konfigurasinya pada node Yudhistira, kemudian kita arahkan IPnya kepada Abimanyu

![4 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/1fded3f9-abf9-4da2-aa98-8aa6b216d3c9)

![4 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/e7b2b798-ccbe-473e-8d25-847e1eaf96db)

![4 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/d6d7cad1-cbae-4af1-a891-ed3b8c179dcb)

![4 4](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/20da2d50-1847-46c8-95ba-f543351d7352)

## 5. Buat juga reverse domain untuk domain utama. (Abimanyu saja yang direverse)
Untuk mereverse DNS, berarti bertujuan pada saat kita menginputkan nilai IP maka akan mengarahkan kepada nama domain yang sudah kita buat. Untuk itu maka kita perlu menjalankan perintah `nano \etc\bind\named.conf.local` dan memasukkan nilai 3 section IP kita secara terbalik.

![5 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/ea0dd47f-3d3d-412d-b1bd-741c6ad886d1)

Kemudian sama halnya dengan DNS biasa, maka kita perlu juga melakukan pengeditan dengan perintah `nano \etc\bind\abimanyud12\3.197.192.in-addr.arpa`

![5 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/a67cf8dc-8c50-4979-aa55-d1c88527cfc6)

Kemudian dapat dilihat pada gambar dibawah bahwa saat kita memasukkan `host -t PTR 192.197.3.4` maka akan mengarah ke abimanyu.d12.com

![5 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/d1134964-d244-497c-a984-30814ec3e614)


## 6. Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama.

![6 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/966a49ab-a66f-4381-a5f2-b5930af44a90)

![6 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/586a47b8-baf7-42ba-be07-de90305b64db)

![6 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/ccc4a68e-ee16-46d0-8513-d854c80196a8)

![6 4](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/a699015f-84c4-4ae1-bf4f-b12dfe8cc85a)


## 7. Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu baratayuda.abimanyu.yyy.com dengan alias www.baratayuda.abimanyu.yyy.com yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda.

![7 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/fa5aff34-c6a5-4dd7-8ea3-4148e42c5e66)
![7 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/d965576a-ceb6-4a1e-b376-a87410f39097)
![7 4](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/9a295789-dc18-4c23-93d9-889500ba57fb)
![7 5](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/e2d2ca3a-7d83-437c-9eb2-58fc78e89211)
![7 6](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/962fb64f-ce9e-4142-9791-4b580f53ca99)
![7 7](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/539a25fb-6c0f-40a1-b3ec-30950296fd4d)

## 8. Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses rjp.baratayuda.abimanyu.yyy.com dengan alias www.rjp.baratayuda.abimanyu.yyy.com yang mengarah ke Abimanyu.
![8 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/897e91d9-cad7-4025-a905-5632e12c2226)


## 9. Arjuna merupakan suatu Load Balancer Nginx dengan tiga worker (yang juga menggunakan nginx sebagai webserver) yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Lakukan deployment pada masing-masing worker.
![9 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/25ca9fb7-85c2-4bb8-a67d-3906bdc9591c)
![9 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/397cc687-dadc-49ed-b941-e9192ced7718)
![9 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/45557cec-73dd-4261-83ef-82130817a937)


## 10. Kemudian gunakan algoritma Round Robin untuk Load Balancer pada Arjuna. Gunakan server_name pada soal nomor 1. Untuk melakukan pengecekan akses alamat web tersebut kemudian pastikan worker yang digunakan untuk menangani permintaan akan berganti ganti secara acak. Untuk webserver di masing-masing worker wajib berjalan di port 8001-8003.
![10 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/a4277f54-47d2-4069-a3a3-b2957a05222a)


## 11. Selain menggunakan Nginx, lakukan konfigurasi Apache Web Server pada worker Abimanyu dengan web server www.abimanyu.yyy.com. Pertama dibutuhkan web server dengan DocumentRoot pada /var/www/abimanyu.yyy
![11 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/3b65df8a-ae04-4e69-aa25-f2c62684ca9c)
![11 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/99b4e4fe-74fc-4b9e-befb-b8f48d790c92)

## 12. Setelah itu ubahlah agar url www.abimanyu.yyy.com/index.php/home menjadi www.abimanyu.yyy.com/home.
![12 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/23849d73-7519-4bcf-9250-bbf0f26269d7)
![12 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/16cf7ee5-4ca0-4df5-98b0-6ca44a31614b)

## 13. Selain itu, pada subdomain www.parikesit.abimanyu.yyy.com, DocumentRoot disimpan pada /var/www/parikesit.abimanyu.yyy
![13 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/ab6de519-7f90-419e-8035-3302a650fa2b)

## 14. Pada subdomain tersebut folder /public hanya dapat melakukan directory listing sedangkan pada folder /secret tidak dapat diakses (403 Forbidden).
![14 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/c4d8c5f0-bb64-4cf0-86fb-cfe8773053a8)
![14 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/54a840cb-896c-4574-8d97-0a5731840dce)
![14 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/30b1b2a5-3930-42c5-9a0e-26c05163921c)

## 15. Buatlah kustomisasi halaman error pada folder /error untuk mengganti error kode pada Apache. Error kode yang perlu diganti adalah 404 Not Found dan 403 Forbidden.
![15 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/cd1aafb2-34ef-4166-be6e-98bc3c21102f)
![15 2](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/5c44c57d-3c34-4d6e-bef5-5785a0f2a5a1)
![15 3](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/6d811668-aeec-473a-99b2-4d788b995413)
![15 4](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/ea0ba4b4-35da-4b3b-8de5-4594520f27fa)
![15 5](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/98582ac7-69b6-4670-888b-18830f00853f)
![15 6](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/5a47775b-d16e-48a2-acc4-1aaad48ebfcd)
![15 7](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/c560d11d-adc5-4a8a-9c60-1aadae14a08b)

## 16. Buatlah suatu konfigurasi virtual host agar file asset www.parikesit.abimanyu.yyy.com/public/js menjadi www.parikesit.abimanyu.yyy.com/js 

![16 1](https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/b4cc1eda-39d8-4898-91ba-381f7f4d9e02)

## 17. Agar aman, buatlah konfigurasi agar www.rjp.baratayuda.abimanyu.yyy.com hanya dapat diakses melalui port 14000 dan 14400.
<img width="522" alt="17 1" src="https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/bc8f6d3a-3bd4-4ab8-b486-5bce428e3124">


## 18. Untuk mengaksesnya buatlah autentikasi username berupa “Wayang” dan password “baratayudayyy” dengan yyy merupakan kode kelompok. Letakkan DocumentRoot pada /var/www/rjp.baratayuda.abimanyu.yyy.
<img width="533" alt="18 1" src="https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/ba0f79e0-3f46-4669-bed7-b98a564f3704">

<img width="508" alt="18 2" src="https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/486de62d-1b0f-44dd-bd04-4ba65040a313">

## 19. Buatlah agar setiap kali mengakses IP dari Abimanyu akan secara otomatis dialihkan ke www.abimanyu.yyy.com (alias)

<img width="467" alt="19 1" src="https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/71423653-4b58-49d8-aace-de83aeb6452e">

## 20. Karena website www.parikesit.abimanyu.yyy.com semakin banyak pengunjung dan banyak gambar gambar random, maka ubahlah request gambar yang memiliki substring “abimanyu” akan diarahkan menuju abimanyu.png.

<img width="515" alt="20 1" src="https://github.com/cchoirun/Jarkom-Modul-2-D12-2023/assets/115228631/809c52aa-8cc6-40a6-925f-a62df5659e7c">

























