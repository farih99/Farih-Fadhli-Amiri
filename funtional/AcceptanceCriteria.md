Berikut DRAFT Acceptance Criteria untuk seluruh **14 User Story** DisiplinGuard. Untuk fitur AI ★, saya masukkan tiga jenis skenario wajib: normal, edge case, dan kegagalan/batas waktu. Nilai **[ASUMSI-08] = rata-rata nilai 100 sebagai batas atas** sengaja ditandai karena rentang nilai akademik belum ditentukan dalam SRS. Selain itu, **NFR-02 hanya menyebut F1-score “memadai” tanpa angka**, sehingga saya tidak menetapkan threshold baru.

# DRAFT Acceptance Criteria DisiplinGuard

## Epik 1. Monitoring Data Siswa

### US-01 — Melihat Data Siswa

**Prioritas:** Must Have
**Traceability:** FR-02

#### Scenario: Data siswa tersedia

```gherkin
Scenario: Menampilkan data siswa yang tersedia
  Given pengguna merupakan Guru BK atau Wali Kelas
  And data siswa tersedia dalam sistem
  When pengguna memilih seorang siswa
  Then sistem menampilkan informasi siswa
  And sistem menampilkan indikator yang berkaitan dengan kedisiplinan
```

**Metode uji:** Black-box testing

#### Scenario: Data siswa tidak tersedia

```gherkin
Scenario: Data siswa tidak ditemukan
  Given pengguna merupakan Guru BK atau Wali Kelas
  And data siswa yang dipilih tidak tersedia
  When pengguna mencoba membuka data siswa tersebut
  Then sistem tidak menampilkan data siswa yang tidak tersedia
  And sistem memberikan informasi bahwa data siswa tidak tersedia
```

**Metode uji:** Black-box testing

---

### US-02 — Melihat Data Absensi

**Prioritas:** Must Have
**Traceability:** FR-03, NFR-04

#### Scenario: Persentase kehadiran tersedia

```gherkin
Scenario: Menampilkan persentase kehadiran siswa
  Given data absensi siswa tersedia
  When pengguna membuka informasi absensi siswa
  Then sistem menampilkan persentase kehadiran siswa
```

**Metode uji:** Black-box testing

#### Scenario: Data absensi belum tersedia

```gherkin
Scenario: Data persentase kehadiran tidak tersedia
  Given data absensi siswa belum tersedia
  When pengguna membuka informasi absensi siswa
  Then sistem tidak menampilkan persentase kehadiran yang tidak tersedia
  And sistem memberikan informasi bahwa data absensi belum tersedia
```

**Metode uji:** Black-box testing

---

### US-03 — Melihat Jumlah Alfa

**Prioritas:** Must Have
**Traceability:** FR-04

#### Scenario: Jumlah alfa tersedia

```gherkin
Scenario: Menampilkan jumlah alfa siswa
  Given data ketidakhadiran tanpa keterangan siswa tersedia
  When pengguna membuka informasi absensi siswa
  Then sistem menampilkan jumlah alfa siswa
```

**Metode uji:** Black-box testing

#### Scenario: Jumlah alfa bernilai nol

```gherkin
Scenario: Menampilkan siswa tanpa alfa
  Given data alfa siswa tersedia
  And jumlah alfa siswa adalah 0
  When pengguna membuka informasi absensi siswa
  Then sistem menampilkan jumlah alfa sebesar 0
```

**Metode uji:** Unit test dan black-box testing

---

### US-04 — Melihat Keterlambatan

**Prioritas:** Must Have
**Traceability:** FR-05

#### Scenario: Jumlah keterlambatan tersedia

```gherkin
Scenario: Menampilkan jumlah keterlambatan siswa
  Given data keterlambatan siswa tersedia
  When pengguna membuka informasi absensi siswa
  Then sistem menampilkan jumlah atau indikator keterlambatan siswa
```

**Metode uji:** Black-box testing

#### Scenario: Jumlah keterlambatan bernilai nol

```gherkin
Scenario: Menampilkan siswa tanpa keterlambatan
  Given data keterlambatan siswa tersedia
  And jumlah keterlambatan siswa adalah 0
  When pengguna membuka informasi absensi siswa
  Then sistem menampilkan jumlah keterlambatan sebesar 0
```

**Metode uji:** Unit test dan black-box testing

---

### US-05 — Melihat Prestasi Akademik

**Prioritas:** Must Have
**Traceability:** FR-06

#### Scenario: Prestasi akademik tersedia

```gherkin
Scenario: Menampilkan prestasi akademik siswa
  Given data prestasi akademik siswa tersedia
  When pengguna membuka informasi siswa
  Then sistem menampilkan informasi prestasi akademik siswa
```

**Metode uji:** Black-box testing

#### Scenario: Data prestasi akademik tidak tersedia

```gherkin
Scenario: Prestasi akademik belum tersedia
  Given data prestasi akademik siswa tidak tersedia
  When pengguna membuka informasi siswa
  Then sistem tidak menampilkan nilai yang tidak tersedia
  And sistem memberikan informasi bahwa data prestasi akademik belum tersedia
```

**Metode uji:** Black-box testing

---

# Epik 2. Deteksi Dini Berbasis AI

## US-06 — Prediksi Tingkat Kedisiplinan ★

**Prioritas:** Must Have
**Traceability:** FR-07, NFR-01, NFR-02, NFR-03

### Scenario: Prediksi berhasil pada data lengkap

```gherkin
Scenario: Menghasilkan prediksi tingkat kedisiplinan
  Given persentase kehadiran siswa tersedia
  And jumlah alfa siswa tersedia
  And jumlah keterlambatan siswa tersedia
  And prestasi akademik atau rata-rata nilai siswa tersedia
  When Guru BK atau Wali Kelas menjalankan prediksi
  Then sistem menghasilkan tepat satu kategori kedisiplinan
  And kategori yang dihasilkan adalah tinggi, sedang, atau rendah
  And hasil prediksi tampil dalam waktu <= 3 detik
```

**Metode uji:** Integration testing dan data evaluation

### Scenario: Data masukan berada pada batas operasional

```gherkin
Scenario: Prediksi dengan kehadiran maksimal dan tanpa ketidakhadiran
  Given persentase kehadiran siswa adalah 100%
  And jumlah alfa siswa adalah 0
  And jumlah keterlambatan siswa adalah 0
  And rata-rata nilai siswa adalah 100 [ASUMSI-08]
  When Guru BK atau Wali Kelas menjalankan prediksi
  Then sistem tidak menolak data yang berada pada batas tersebut
  And sistem menghasilkan satu kategori kedisiplinan
  And hasil prediksi tampil dalam waktu <= 3 detik
```

**Metode uji:** Unit test dan integration testing

> **Catatan:** nilai akademik 100 digunakan sebagai [ASUMSI-08] karena SRS belum menetapkan rentang nilai akademik.

### Scenario: AI gagal merespons tepat waktu

```gherkin
Scenario: Prediksi melebihi batas waktu
  Given seluruh data minimum prediksi tersedia
  When pengguna menjalankan prediksi
  And sistem belum memberikan hasil setelah 3 detik
  Then sistem tidak menampilkan hasil prediksi sebagai hasil final
  And sistem memberikan informasi bahwa proses prediksi belum berhasil diselesaikan
```

**Metode uji:** Integration testing dan performance testing

### Scenario: Evaluasi akurasi model

```gherkin
Scenario: Evaluasi akurasi model memenuhi target
  Given tersedia data pengujian model
  When model dievaluasi terhadap data pengujian
  Then akurasi model tercatat >= 77%
  And F1-score dicatat pada hasil evaluasi
```

**Metode uji:** Data evaluation

**Catatan:** SRS belum memberikan angka minimum untuk F1-score. Karena itu, acceptance criterion hanya mewajibkan F1-score dilaporkan, bukan menetapkan angka baru.

---

## US-07 — Melihat Skor Risiko ★

**Prioritas:** Must Have
**Traceability:** FR-08, NFR-01

### Scenario: Skor risiko tersedia setelah prediksi

```gherkin
Scenario: Menampilkan skor risiko
  Given prediksi tingkat kedisiplinan siswa telah berhasil
  When sistem menyelesaikan proses prediksi
  Then sistem menampilkan skor risiko siswa
  And skor tersebut ditampilkan bersama hasil prediksi
```

**Metode uji:** Integration testing

### Scenario: Prediksi gagal

```gherkin
Scenario: Skor risiko tidak ditampilkan ketika prediksi gagal
  Given proses prediksi tingkat kedisiplinan tidak berhasil
  When sistem menyelesaikan proses tanpa hasil prediksi
  Then sistem tidak menampilkan skor risiko sebagai hasil valid
```

**Metode uji:** Integration testing

### Scenario: Skor risiko dapat digunakan untuk menentukan prioritas

```gherkin
Scenario: Skor risiko tampil untuk mendukung pemantauan
  Given hasil prediksi siswa tersedia
  When Guru BK atau Wali Kelas membuka hasil prediksi
  Then skor risiko dapat dilihat oleh pengguna
  And skor tersebut dapat digunakan sebagai informasi pendukung untuk menentukan prioritas pemantauan
```

**Metode uji:** UAT

---

## US-08 — Mendapatkan Rekomendasi Intervensi ★

**Prioritas:** Must Have
**Traceability:** FR-09, NFR-11

### Scenario: Rekomendasi tersedia

```gherkin
Scenario: Menampilkan rekomendasi intervensi
  Given hasil prediksi tingkat kedisiplinan siswa tersedia
  When pengguna membuka hasil prediksi
  Then sistem menampilkan rekomendasi intervensi
  And rekomendasi diberikan berdasarkan kategori risiko atau hasil prediksi
```

**Metode uji:** Integration testing dan UAT

### Scenario: Siswa berisiko memiliki rekomendasi

```gherkin
Scenario: Siswa berisiko memperoleh rekomendasi tindak lanjut
  Given siswa telah teridentifikasi sebagai siswa berisiko
  When sistem menyelesaikan proses prediksi
  Then sistem menyediakan rekomendasi tindak lanjut untuk siswa tersebut
```

**Metode uji:** Data evaluation

### Scenario: Cakupan rekomendasi memenuhi target

```gherkin
Scenario: Minimal 70 persen siswa berisiko memiliki rekomendasi
  Given terdapat daftar siswa yang teridentifikasi berisiko
  When sistem dievaluasi terhadap seluruh siswa berisiko
  Then minimal 70% siswa berisiko memiliki rekomendasi tindak lanjut
```

**Metode uji:** Data evaluation

### Scenario: AI gagal menghasilkan rekomendasi

```gherkin
Scenario: Rekomendasi tidak ditampilkan tanpa hasil prediksi
  Given sistem tidak berhasil menghasilkan prediksi tingkat kedisiplinan
  When pengguna membuka hasil prediksi
  Then sistem tidak menampilkan rekomendasi sebagai hasil valid
  And sistem memberikan informasi bahwa rekomendasi belum dapat diberikan
```

**Metode uji:** Integration testing

---

# Epik 3. Prioritas Pemantauan

## US-09 — Melihat Faktor yang Berkaitan dengan Prediksi

**Prioritas:** Should Have
**Traceability:** FR-11

### Scenario: Faktor prediksi tersedia

```gherkin
Scenario: Menampilkan faktor yang berkaitan dengan prediksi
  Given hasil prediksi siswa tersedia
  When pengguna membuka detail prediksi
  Then sistem menampilkan ringkasan faktor yang berkaitan dengan hasil prediksi
```

**Metode uji:** Inspection dan UAT

### Scenario: Hasil prediksi tidak tersedia

```gherkin
Scenario: Detail faktor tidak tersedia tanpa prediksi
  Given sistem belum menghasilkan prediksi siswa
  When pengguna membuka detail prediksi
  Then sistem tidak menampilkan faktor sebagai hasil prediksi
```

**Metode uji:** Black-box testing

---

## US-10 — Melihat Daftar Siswa Berisiko

**Prioritas:** Must Have
**Traceability:** FR-10, NFR-05

### Scenario: Daftar siswa berisiko tersedia

```gherkin
Scenario: Menampilkan daftar siswa berisiko
  Given terdapat siswa yang telah memiliki hasil prediksi
  When Guru BK atau Wali Kelas membuka daftar prioritas
  Then sistem menampilkan siswa yang memiliki risiko kedisiplinan
```

**Metode uji:** Black-box testing

### Scenario: Pengguna berhasil menemukan siswa berisiko

```gherkin
Scenario: Pengguna menemukan siswa berisiko melalui daftar prioritas
  Given daftar siswa berisiko tersedia
  When pengguna melakukan tugas pencarian siswa berisiko
  Then minimal 80% pengguna uji dapat menemukan siswa berisiko melalui sistem
```

**Metode uji:** UAT

### Scenario: Tidak terdapat siswa berisiko

```gherkin
Scenario: Daftar prioritas kosong
  Given tidak terdapat siswa yang teridentifikasi berisiko
  When pengguna membuka daftar prioritas
  Then sistem menampilkan kondisi bahwa tidak terdapat siswa berisiko pada data yang sedang dipantau
```

**Metode uji:** Black-box testing

---

## US-11 — Memfilter Siswa

**Prioritas:** Should Have
**Traceability:** FR-12

### Scenario: Filter berdasarkan kelas berhasil

```gherkin
Scenario: Memfilter siswa berdasarkan kelas
  Given data siswa memiliki informasi kelas
  When pengguna memilih suatu kelas sebagai filter
  Then sistem hanya menampilkan data siswa yang sesuai dengan kelas tersebut
```

**Metode uji:** Black-box testing

### Scenario: Filter berdasarkan jurusan berhasil

```gherkin
Scenario: Memfilter siswa berdasarkan jurusan
  Given data siswa memiliki informasi jurusan
  When pengguna memilih suatu jurusan sebagai filter
  Then sistem hanya menampilkan data siswa yang sesuai dengan jurusan tersebut
```

**Metode uji:** Black-box testing

### Scenario: Filter menghasilkan data kosong

```gherkin
Scenario: Tidak terdapat siswa yang sesuai dengan filter
  Given pengguna telah memilih filter tertentu
  When tidak terdapat siswa yang memenuhi filter tersebut
  Then sistem tidak menampilkan data siswa yang tidak sesuai
  And sistem menampilkan kondisi bahwa tidak terdapat data yang sesuai
```

**Metode uji:** Black-box testing

---

## US-12 — Menggunakan Sistem melalui Smartphone

**Prioritas:** Should Have
**Traceability:** FR-14, NFR-04

### Scenario: Fungsi utama dapat digunakan melalui smartphone

```gherkin
Scenario: Mengakses fungsi utama melalui smartphone
  Given pengguna mengakses DisiplinGuard melalui browser smartphone
  When pengguna membuka fungsi utama sistem
  Then fungsi utama dapat digunakan melalui smartphone
```

**Metode uji:** UAT dan compatibility testing

### Scenario: Pemantauan siswa melalui smartphone

```gherkin
Scenario: Melihat data siswa melalui smartphone
  Given pengguna telah membuka DisiplinGuard melalui smartphone
  When pengguna memilih seorang siswa
  Then sistem menampilkan informasi siswa dan indikator kedisiplinan
```

**Metode uji:** Compatibility testing

---

# Epik 4. Pemantauan dan Tindak Lanjut

## US-13 — Mencatat Riwayat Pemantauan

**Prioritas:** Should Have
**Traceability:** FR-13

### Scenario: Riwayat pemantauan berhasil disimpan

```gherkin
Scenario: Menyimpan riwayat pemantauan siswa
  Given pengguna sedang melakukan pemantauan siswa
  When pengguna mencatat tindak lanjut
  Then sistem menyimpan catatan tersebut sebagai riwayat pemantauan siswa
```

**Metode uji:** Integration testing

### Scenario: Riwayat pemantauan dapat dilihat kembali

```gherkin
Scenario: Melihat riwayat pemantauan siswa
  Given riwayat pemantauan siswa telah tersimpan
  When pengguna membuka riwayat siswa
  Then sistem menampilkan riwayat pemantauan yang telah tersimpan
```

**Metode uji:** Black-box testing

### Scenario: Penyimpanan riwayat gagal

```gherkin
Scenario: Riwayat tidak berhasil disimpan
  Given pengguna telah melakukan pencatatan tindak lanjut
  When proses penyimpanan gagal
  Then sistem tidak menyatakan catatan telah tersimpan
  And sistem memberikan informasi bahwa proses penyimpanan gagal
```

**Metode uji:** Integration testing

---

# Epik 5. Ringkasan Kondisi

## US-14 — Melihat Dashboard Kondisi Kedisiplinan

**Prioritas:** Must Have
**Traceability:** FR-01, NFR-05, NFR-06

### Scenario: Dashboard berhasil ditampilkan

```gherkin
Scenario: Menampilkan ringkasan kondisi kedisiplinan
  Given data siswa tersedia
  When Guru BK atau Wali Kelas membuka dashboard
  Then sistem menampilkan ringkasan kondisi kedisiplinan siswa
```

**Metode uji:** Black-box testing

### Scenario: Dashboard membantu menemukan siswa berisiko

```gherkin
Scenario: Menemukan siswa berisiko melalui dashboard
  Given data siswa berisiko tersedia
  When pengguna melakukan tugas pemantauan melalui dashboard
  Then minimal 80% pengguna uji dapat menemukan siswa berisiko
```

**Metode uji:** UAT

### Scenario: Pengguna merasa pemantauan lebih mudah

```gherkin
Scenario: Pemantauan dinilai lebih mudah setelah menggunakan dashboard
  Given pengguna uji telah menggunakan dashboard DisiplinGuard
  When pengguna mengisi evaluasi kemudahan pemantauan
  Then minimal 70% pengguna uji menyatakan pemantauan lebih mudah
```

**Metode uji:** UAT dan usability testing

---

# Ringkasan Coverage Acceptance Criteria

| User Story  | Skenario | Metode Uji Utama                            |
| ----------- | -------: | ------------------------------------------- |
| US-01       |        2 | Black-box                                   |
| US-02       |        2 | Black-box                                   |
| US-03       |        2 | Unit + Black-box                            |
| US-04       |        2 | Unit + Black-box                            |
| US-05       |        2 | Black-box                                   |
| **US-06 ★** |    **4** | Integration + Data Evaluation + Performance |
| **US-07 ★** |    **3** | Integration + UAT                           |
| **US-08 ★** |    **4** | Integration + Data Evaluation + UAT         |
| US-09       |        2 | Inspection + UAT                            |
| US-10       |        3 | Black-box + UAT                             |
| US-11       |        3 | Black-box                                   |
| US-12       |        2 | UAT + Compatibility                         |
| US-13       |        3 | Integration + Black-box                     |
| US-14       |        3 | Black-box + UAT                             |

## Catatan QA Penting

Ada dua hal yang **belum dapat dijadikan angka acceptance criterion tanpa membuat asumsi baru**:

1. **NFR-02 F1-score** hanya menyebut target *“memadai”*. Jadi angka seperti F1 ≥ 0,70 tidak boleh dimasukkan tanpa dasar riset atau keputusan stakeholder.
2. **Rentang nilai akademik** tidak diberikan. Karena prompt meminta edge case numerik, penggunaan **rata-rata nilai 100** diberi label **[ASUMSI-08]**. Nilai ini sebaiknya dikonfirmasi sebelum SRS/Test Case final.

Dengan demikian, acceptance criteria tetap cukup konkret untuk diturunkan menjadi **Test Case**, tetapi tidak menyamarkan asumsi sebagai persyaratan yang sudah disepakati.
