# DRAF User Stories DisiplinGuard

User Stories berikut diturunkan langsung dari SRS DisiplinGuard. Setiap story hanya mencakup fitur **Must Have** dan **Should Have**, serta ditelusurkan kembali ke FR dan NFR yang relevan. 

## Epik 1: Monitoring Data Siswa

### US-01: Melihat data siswa

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat data siswa beserta indikator yang berkaitan dengan kedisiplinan, **Sehingga** saya dapat memahami kondisi siswa sebelum menentukan tindak lanjut.

**Prioritas:** Must Have
**Keterlacakan:** FR-02

### US-02: Melihat data absensi

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat persentase kehadiran siswa, **Sehingga** saya dapat mengetahui kondisi kehadiran siswa sebagai salah satu indikator kedisiplinan.

**Prioritas:** Must Have
**Keterlacakan:** FR-03, NFR-04

### US-03: Melihat jumlah alfa

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat jumlah ketidakhadiran siswa tanpa keterangan, **Sehingga** saya dapat mengenali pola ketidakhadiran yang berpotensi berkaitan dengan masalah kedisiplinan.

**Prioritas:** Must Have
**Keterlacakan:** FR-04

### US-04: Melihat keterlambatan

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat indikator atau jumlah keterlambatan siswa, **Sehingga** saya dapat mempertimbangkan keterlambatan sebagai bagian dari pemantauan kedisiplinan.

**Prioritas:** Must Have
**Keterlacakan:** FR-05

### US-05: Melihat prestasi akademik

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat informasi prestasi akademik siswa, **Sehingga** saya dapat mempertimbangkan hubungan prestasi akademik dengan kondisi kedisiplinan siswa.

**Prioritas:** Must Have
**Keterlacakan:** FR-06

---

# Epik 2: Deteksi Dini Berbasis AI

### US-06: Prediksi tingkat kedisiplinan ★

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** memperoleh prediksi tingkat kedisiplinan siswa berdasarkan indikator absensi dan prestasi akademik, **Sehingga** saya dapat lebih cepat mengidentifikasi siswa yang berpotensi mengalami masalah kedisiplinan.

**Prioritas:** Must Have
**Keterlacakan:** FR-07, NFR-01, NFR-02

### US-07: Melihat skor risiko ★

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat skor risiko siswa setelah prediksi dilakukan, **Sehingga** saya dapat memahami tingkat risiko dan menentukan prioritas pemantauan.

**Prioritas:** Must Have
**Keterlacakan:** FR-08, NFR-01

### US-08: Mendapatkan rekomendasi intervensi ★

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** memperoleh rekomendasi intervensi berdasarkan hasil prediksi, **Sehingga** saya memiliki bahan pertimbangan untuk melakukan tindak lanjut secara preventif.

**Prioritas:** Must Have
**Keterlacakan:** FR-09, NFR-11

### US-09: Melihat faktor yang berkaitan dengan prediksi

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat ringkasan faktor yang berhubungan dengan hasil prediksi siswa, **Sehingga** saya dapat memahami kondisi yang mendasari hasil prediksi sebelum menentukan tindak lanjut.

**Prioritas:** Should Have
**Keterlacakan:** FR-11

---

# Epik 3: Prioritas Pemantauan

### US-10: Melihat daftar siswa berisiko

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat daftar siswa yang memiliki risiko kedisiplinan, **Sehingga** saya dapat memprioritaskan siswa yang membutuhkan perhatian lebih dahulu.

**Prioritas:** Must Have
**Keterlacakan:** FR-10, NFR-05

### US-11: Memfilter siswa

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** menyaring data siswa berdasarkan kelas, jurusan, atau kategori risiko, **Sehingga** saya dapat memfokuskan pemantauan pada kelompok siswa tertentu.

**Prioritas:** Should Have
**Keterlacakan:** FR-12

### US-12: Menggunakan sistem melalui smartphone

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** menggunakan fungsi utama DisiplinGuard melalui smartphone, **Sehingga** saya tetap dapat melakukan pemantauan ketika tidak menggunakan komputer sekolah.

**Prioritas:** Should Have
**Keterlacakan:** FR-14, NFR-04

---

# Epik 4: Pemantauan dan Tindak Lanjut

### US-13: Mencatat riwayat pemantauan

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** menyimpan riwayat pemantauan dan tindak lanjut siswa, **Sehingga** saya dapat melihat catatan penanganan siswa secara berkelanjutan.

**Prioritas:** Should Have
**Keterlacakan:** FR-13

---

# Epik 5: Ringkasan Kondisi

### US-14: Melihat dashboard kondisi kedisiplinan

**Sebagai** Guru BK atau Wali Kelas, **Saya ingin** melihat ringkasan kondisi kedisiplinan pada dashboard, **Sehingga** saya dapat memperoleh gambaran kondisi siswa secara cepat tanpa menganalisis data mentah satu per satu.

**Prioritas:** Must Have
**Keterlacakan:** FR-01, NFR-05, NFR-06

---

## Rekapitulasi User Stories

| Epik                       | ID    | User Story                                    | Prioritas   | AI    |
| -------------------------- | ----- | --------------------------------------------- | ----------- | ----- |
| Monitoring Data Siswa      | US-01 | Melihat data siswa                            | Must Have   | Tidak |
| Monitoring Data Siswa      | US-02 | Melihat persentase kehadiran                  | Must Have   | Tidak |
| Monitoring Data Siswa      | US-03 | Melihat jumlah alfa                           | Must Have   | Tidak |
| Monitoring Data Siswa      | US-04 | Melihat keterlambatan                         | Must Have   | Tidak |
| Monitoring Data Siswa      | US-05 | Melihat prestasi akademik                     | Must Have   | Tidak |
| Deteksi Dini AI            | US-06 | Prediksi tingkat kedisiplinan                 | Must Have   | ★     |
| Deteksi Dini AI            | US-07 | Melihat skor risiko                           | Must Have   | ★     |
| Deteksi Dini AI            | US-08 | Mendapatkan rekomendasi intervensi            | Must Have   | ★     |
| Deteksi Dini AI            | US-09 | Melihat faktor yang berkaitan dengan prediksi | Should Have | Tidak |
| Prioritas Pemantauan       | US-10 | Melihat daftar siswa berisiko                 | Must Have   | Tidak |
| Prioritas Pemantauan       | US-11 | Memfilter siswa                               | Should Have | Tidak |
| Prioritas Pemantauan       | US-12 | Menggunakan sistem melalui smartphone         | Should Have | Tidak |
| Pemantauan & Tindak Lanjut | US-13 | Mencatat riwayat pemantauan                   | Should Have | Tidak |
| Ringkasan Kondisi          | US-14 | Melihat dashboard kondisi kedisiplinan        | Must Have   | Tidak |

SRS menetapkan fitur AI inti berupa **prediksi tingkat kedisiplinan, skor risiko, dan rekomendasi intervensi**, sedangkan daftar prioritas, detail siswa, filter, riwayat pemantauan, dan akses mobile termasuk fitur yang berada dalam scope Must Have atau Should Have. 

### Catatan keterlacakan

Tidak semua NFR perlu menjadi sumber user story secara langsung. NFR seperti keamanan, privasi, reliability, dan maintainability lebih tepat diperlakukan sebagai **kriteria kualitas sistem** yang membatasi implementasi user story, bukan kebutuhan fungsional yang berdiri sebagai story tersendiri. NFR tersebut tetap berasal dari SRS. 
