# Jarkom_Modul1_Lapres_A02

## Soal 1
Sebutkan web server yang digunakan pada "testing.mekanis.me"!
### Jawab
- #### Display Filter
  `ip.src == 157.245.50.224 && http.server`
- #### Penjelasan
  Menggunakan `ip.src == 157.245.50.224` yang akan menampilkan paket-paket yang berasal dari IP 157.245.50.224, IP dari website "testing.mekanis.me". Filter expression tersebut digabungkan dengan `http.server` yang menampilkan paket yang berisi info mengenai server website.
- #### Screenshot
  ![soal1](/images/soal1.jpg)
  
## Soal 2
Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!
### Jawab
- #### Display Filter
  `http contains Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg`
- #### Penjelasan
  Filter expression akan menampilkan paket yang berisi file "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg" Setelah itu klik menu File > Export Objects > HTTP, simpan file.
- #### Screenshot
  ![soal2-1](/images/soal2-1.jpg)
  ![soal2-2](/images/soal2-2.jpg)
  ![soal2-3](/images/Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg)
  
## Soal 3
Cari username dan password ketika login di "ppid.dpr.go.id"!
### Jawab
- #### Display Filter
  `http.host == ppid.dpr.go.id && http.request.method == POST`
- #### Penjelasan
  Filter expression akan menampilkan paket yang menuju web "ppid.drp.go.id" dan memiliki request method POST. Didapat bahwa username = 10pemuda dan password = guncangdunia
- #### Screenshot
  ![soal3](/images/soal3.jpg)
  
## Soal 4
Temukan paket dari web-web yang menggunakan basic authentication method!
### Jawab
- #### Display Filter
  `http.authbasic` lalu `ip.src == 157.245.50.224`
- #### Penjelasan
  Filter expression pertama akan menampilkan paket dengan website mana saja yang menggunakan basic authentication method. Selanjutnya didapat IP dari website-website tersebut, yakni 157.245.50.224. Dilanjutkan dengan `ip.src == 157.245.50.224` untuk menampilkan paket-paket yang berasal dari website-website yang menggunakan basic authentication method.
- #### Screenshot
  ![soal4-1](/images/soal4-1.jpg)
  ![soal4-2](/images/soal4-2.jpg)
  
## Soal 5
Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!
### Jawab
- #### Display Filter
  `http.host == aku.pengen.pw`
- #### Penjelasan
  Filter expression akan menampilkan paket yang menuju web "aku.pengen.pw". Selanjutnya didapatkan melalui Credentials pada Authorization bahwa username = kakakgamtenk dan password = hartatahtabermuda. Berikutnya setelah login, terdapat soal "Sebutkan urutan konfigurasi pengkabelan T56B" yang jawabannya dapat dilihat pada screenshot di bawah.
- #### Screenshot
  ![soal5-1](/images/soal5-1.jpg)
  ![soal5-2](/images/soal5-2.jpg)
  
## Soal 6
Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).
### Jawab
- #### Display Filter
  `ftp-data.command contains "STOR Answer.zip"`
  `ftp-data.command contains "zipkey.txt"`
- #### Penjelasan
  Pertama-tama, dilakukan pencarian untuk data pengiriman file FTP dengan display filter pertama. Paket yang ditemukan pada display filter pertama kemudian dilakukan "Follow TCP Stream" untuk mendapatkan keseluruhan data dari semua paket untuk file tersebut. File ini dapat kemudian di-save sebagai ZIP. Kemudian, display filter kedua digunakan untuk mendapatkan data file kedua, zipkey.txt. Dengan cara yang sama, file dibuka untuk membaca datanya yang mengandung kode password ZIPnya, sehingga dapat dibuka.
- #### Screenshot
  ![soal6-1](/images/soal6-1.jpg)
  ![soal6-2](/images/soal6-2.jpg)
  ![soal6-3](/images/soal6-3.jpg)
  
## Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut.
Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"
### Jawab
- #### Display Filter
  `frame contains "Yes.pdf"`
- #### Penjelasan
  Suatu file apabila di-zip akan tetap memiliki data nama file apa saja yang berada di dalam zip tersebut. Maka, dengan melakukan pencarian langsung terhadap byte-byte paket, dapat ditemukan file yang membawa data Yes.pdf. Paket tersebut dapat menunjukkan file apa yang menampung Yes.pdf tersebut, maka dilakukan follow TCP Stream untuk mendownload data yang sesuai. Didapatkan nama file yaitu 473.zip.
- #### Screenshot
  ![soal7-1](/images/soal7-1.jpg)
  ![soal7-2](/images/soal7-2.jpg)
  
## Soal 8
Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!
### Jawab
- #### Display Filter
  `ftp.response.code == 220`
  `ip.src == 198.246.117.106 and ftp-data.command contains "RETR"`
- #### Penjelasan
  Pertama dilakukan pencarian untuk paket-paket yang berisi pesan jawaban dari server-server FTP yang dihubungi, di mana pesan tersebut merupakan welcome message dari server dengan mencari kode response 220. Kemudian, dilakukan pencarian paket dengan IP yang sesuai, dan dengan syarat kedua yaitu paket membawa data yang berkaitan dengan perintah RETR. Ditemukan bahwa objek yang didownload adalah Readme.
- #### Screenshot
  ![soal8-1](/images/soal8-1.jpg)
  ![soal8-2](/images/soal8-2.jpg)
  
## Soal 9
Cari username dan password ketika login FTP pada localhost!
### Jawab
- #### Display Filter
  `ftp.request.command == USER or ftp.request.command == PASS`
- #### Penjelasan
  Pencarian paket dilakukan dengan memfilter perintah FTP antara USER atau PASS, untuk mendapatkan username dan password FTP yang digunakan (dikirim sebagai request). Didapatkan username dhana dan password dhana123.
- #### Screenshot
  ![soal9-1](/images/soal9-1.jpg)
  
## Soal 10
Cari file .pdf di wireshark lalu download dan buka file tersebut!
clue: "25 50 44 46" 
### Jawab
- #### Display Filter
  `frame contains "\x25\x50\x44\x46"`
- #### Penjelasan
  Pencarian paket dilakukan dengan secara langsung mencari paket yang datanya mengandung nilai hex 25 50 44 46, yang merupakan tanda bahwa terdapat data file PDF di dalam paket tersebut. Kemudian, dilakukan follow TCP stream untuk mendapatkan keseluruhan paket-paket yang digunakan dalam satu koneksi TCP ini, sehingga file dapat didownload secara utuh. File merupakan dokumen terkait undang-undang.
- #### Screenshot
  ![soal10-1](/images/soal10-1.jpg)
  ![soal10-2](/images/soal10-2.jpg)

## Soal 11
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
### Jawab
- #### Capture Filter
  `port 21`
- #### Penjelasan
  Capture filter tersebut menangkap paket dengan tujuan maupun asal port 21 (FTP).
- #### Screenshot
  ![soal11-1](/images/soal11-1.jpg)

## Soal 12
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
### Jawab
- #### Capture Filter
  `src port 80`
- #### Penjelasan
  Dengan kata kunci src maka dapat mengambil hanya yang berasal dari port 80 (HTTP).
- #### Screenshot
  ![soal12-1](/images/soal12-1.jpg)

## Soal 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
### Jawab
- #### Capture Filter
  `dst port 443`
- #### Penjelasan
  Dengan akta kunci dst maka dapat mengambil hanya yang menuju port 443 (HTTPS).
- #### Screenshot
  ![soal13-1](/images/soal13-1.jpg)

## Soal 14
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
### Jawab
- #### Capture Filter
  `src host 192.168.1.11`
- #### Penjelasan
  Pertama, dilakukan pencarian untuk IP masing-masing dengan menggunakan Command Prompt dengan perintah `ipconfig`. Setelah didapat, dapat digunakan sebagai filter dengan kata kunci src untuk sumber.
- #### Screenshot
  ![soal14-1](/images/soal14-1.jpg)
  ![soal14-2](/images/soal14-2.jpg)

## Soal 15
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!
### Jawab
- #### Capture Filter
  `dst host monta.if.its.ac.id`
- #### Penjelasan
  Menggunakan kata kunci dst untuk mencari paket dengan tujuan yang diberikan, dalam kasus ini monta.if.its.ac.id. Host tidak harus dalam bentuk IP.
- #### Screenshot
  ![soal15-1](/images/soal15-1.jpg)
