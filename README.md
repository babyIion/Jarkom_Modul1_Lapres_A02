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
