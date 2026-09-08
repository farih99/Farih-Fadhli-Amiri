# DRAF SRS Ringkas DisiplinGuard

Dokumen ini merupakan turunan langsung dari PRD DisiplinGuard pada bahan yang diberikan. Batasan kebutuhan dibuat hanya berdasarkan informasi yang tersedia pada PRD. 

## 1. Tujuan, Scope, dan Definisi Istilah

### 1.1 Tujuan

SRS ini mendefinisikan kebutuhan sistem DisiplinGuard sebagai sistem *early-warning* yang membantu Guru BK dan Wali Kelas mengidentifikasi siswa yang berisiko mengalami penurunan kedisiplinan berdasarkan pola absensi dan prestasi akademik. Sistem berfungsi sebagai pendukung keputusan dan tidak menggantikan keputusan guru. 

### 1.2 Scope

Scope prototype mencakup:

* pemantauan data siswa
* pemantauan absensi
* pemantauan prestasi akademik
* prediksi tingkat kedisiplinan
* skor risiko
* rekomendasi intervensi
* daftar prioritas siswa berisiko
* detail siswa
* filter siswa
* riwayat pemantauan
* akses melalui browser desktop dan smartphone

Fitur tersebut mengacu pada pembagian prioritas MoSCoW pada PRD. 

Di luar scope prototype adalah otomatisasi keputusan disipliner, integrasi kompleks dengan seluruh sistem sekolah, dan penggunaan model AI yang kompleks. 

### 1.3 Definisi Istilah

| Istilah                   | Definisi                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| **DisiplinGuard**         | Sistem pendukung keputusan berbasis AI untuk deteksi dini risiko kedisiplinan siswa               |
| **Early-warning**         | Mekanisme identifikasi awal terhadap siswa yang berpotensi mengalami masalah kedisiplinan         |
| **Prediksi kedisiplinan** | Hasil klasifikasi kondisi siswa menjadi tinggi, sedang, atau rendah                               |
| **Skor risiko**           | Representasi tingkat risiko siswa berdasarkan hasil prediksi                                      |
| **Alfa**                  | Ketidakhadiran siswa tanpa keterangan                                                             |
| **Intervensi**            | Tindak lanjut pembinaan yang dipertimbangkan guru berdasarkan hasil sistem                        |
| **Primary user**          | Guru BK dan Wali Kelas                                                                            |
| **AI**                    | Fitur klasifikasi yang digunakan untuk mengidentifikasi pola dan memprediksi tingkat kedisiplinan |

---

# 2. User, Stakeholder, Lingkungan Operasi, Asumsi & Dependensi

## 2.1 User dan Stakeholder

| Peran                                 | Kebutuhan Utama                                                       | Tingkat Pengaruh |
| ------------------------------------- | --------------------------------------------------------------------- | ---------------- |
| Guru BK                               | Mengetahui siswa berisiko, tingkat risiko, dan rekomendasi intervensi | Tinggi           |
| Wali Kelas                            | Memantau kondisi kedisiplinan siswa secara cepat                      | Tinggi           |
| Kepala Sekolah                        | Mendapatkan gambaran umum kondisi kedisiplinan                        | Tinggi           |
| Wakil Kepala Sekolah Bidang Kesiswaan | Memantau pola kedisiplinan untuk evaluasi dan pembinaan               | Tinggi           |
| Manajemen Sekolah                     | Informasi pendukung pengambilan keputusan                             | Sedang           |
| Guru Mata Pelajaran                   | Informasi relevan untuk mendukung pemantauan siswa                    | Sedang           |

Guru BK dan Wali Kelas merupakan **primary user**, sedangkan stakeholder lainnya merupakan **secondary user**. 

## 2.2 Lingkungan Operasi

Sistem ditujukan untuk berjalan pada **platform web** dengan dukungan **mobile-responsive**, sehingga dapat diakses menggunakan browser pada komputer sekolah maupun smartphone guru. 

Detail sistem operasi, browser minimum, spesifikasi perangkat, dan kebutuhan jaringan **belum ditentukan dalam PRD** sehingga tidak ditambahkan ke SRS.

## 2.3 Asumsi dan Dependensi

| Kode | Asumsi/Dependensi                                                                       |
| ---- | --------------------------------------------------------------------------------------- |
| A-01 | Guru BK dan Wali Kelas memiliki akses terhadap data absensi dan prestasi akademik       |
| A-02 | Kategori kedisiplinan tinggi, sedang, dan rendah digunakan sebagai kategori operasional |
| A-03 | Hasil rekomendasi digunakan sebagai bahan pertimbangan guru                             |
| A-04 | Prototype dapat menggunakan data historis yang tersedia                                 |
| A-05 | Pengguna dapat menggunakan browser melalui komputer atau smartphone                     |

Asumsi tersebut berasal dari PRD dan tidak ditambahkan asumsi baru. 

---

# 3. Functional Requirements

Metode verifikasi yang digunakan:

* **UAT**: pengujian penerimaan pengguna
* **Black-box**: pengujian berdasarkan input dan output
* **Inspection**: pemeriksaan keluaran atau tampilan data
* **Data evaluation**: evaluasi menggunakan data pengujian

| ID          | Functional Requirement                                                                                                                                                 | Prioritas   | Metode Verifikasi |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ----------------- |
| **FR-01**   | Sistem harus dapat menampilkan ringkasan kondisi kedisiplinan siswa saat pengguna membuka dashboard → sistem menampilkan informasi kondisi kedisiplinan secara ringkas | Must Have   | UAT               |
| **FR-02**   | Sistem harus dapat menampilkan data siswa saat pengguna memilih data siswa → sistem menampilkan informasi siswa dan indikator terkait kedisiplinan                     | Must Have   | Black-box         |
| **FR-03**   | Sistem harus dapat menampilkan persentase kehadiran siswa saat pengguna melihat data absensi → sistem menampilkan persentase kehadiran                                 | Must Have   | Black-box         |
| **FR-04**   | Sistem harus dapat menampilkan jumlah alfa siswa saat pengguna melihat data absensi → sistem menampilkan jumlah ketidakhadiran tanpa keterangan                        | Must Have   | Black-box         |
| **FR-05**   | Sistem harus dapat menampilkan data keterlambatan saat pengguna melihat data absensi → sistem menampilkan jumlah atau indikator keterlambatan                          | Must Have   | Black-box         |
| **FR-06**   | Sistem harus dapat menampilkan indikator prestasi akademik saat pengguna melihat data siswa → sistem menampilkan informasi prestasi akademik                           | Must Have   | Black-box         |
| **FR-07** ★ | Sistem harus dapat memprediksi tingkat kedisiplinan saat data indikator siswa tersedia → sistem menghasilkan kategori tinggi, sedang, atau rendah                      | Must Have   | Data evaluation   |
| **FR-08** ★ | Sistem harus dapat menghasilkan skor risiko saat hasil prediksi kedisiplinan tersedia → sistem menampilkan representasi tingkat risiko siswa                           | Must Have   | Data evaluation   |
| **FR-09** ★ | Sistem harus dapat memberikan rekomendasi intervensi saat hasil prediksi tersedia → sistem menampilkan saran tindak lanjut berdasarkan kategori risiko                 | Must Have   | UAT               |
| **FR-10**   | Sistem harus dapat menampilkan daftar prioritas siswa berisiko saat pengguna melakukan pemantauan → sistem menampilkan siswa yang perlu ditindaklanjuti                | Must Have   | UAT               |
| **FR-11**   | Sistem harus dapat menampilkan detail faktor yang berhubungan dengan prediksi saat pengguna membuka detail siswa → sistem menampilkan ringkasan faktor relevan         | Should Have | Inspection        |
| **FR-12**   | Sistem harus dapat melakukan penyaringan siswa saat pengguna memilih kelas, jurusan, atau kategori risiko → sistem menampilkan data sesuai filter                      | Should Have | Black-box         |
| **FR-13**   | Sistem harus dapat menyimpan riwayat pemantauan saat pengguna melakukan pencatatan tindak lanjut → sistem menyediakan riwayat pemantauan                               | Should Have | Black-box         |
| **FR-14**   | Sistem harus dapat menampilkan fungsi utama pada perangkat smartphone saat pengguna mengakses sistem melalui browser mobile → fungsi utama tetap dapat digunakan       | Should Have | UAT               |
| **FR-15**   | Sistem harus dapat menampilkan ringkasan kondisi satu kelas saat fitur ringkasan kelas digunakan → sistem menampilkan gambaran kondisi kedisiplinan kelas              | Could Have  | Inspection        |
| **FR-16**   | Sistem harus dapat menampilkan ringkasan kondisi untuk pimpinan saat fitur ringkasan pimpinan digunakan → sistem menampilkan informasi agregat untuk pemantauan        | Could Have  | Inspection        |
| **FR-17**   | Sistem harus dapat memberikan notifikasi risiko saat terdapat siswa dengan risiko tertentu → sistem memberikan pemberitahuan kepada pengguna                           | Could Have  | Black-box         |

Fitur FR-07 sampai FR-09 diberi tanda ★ karena merupakan fitur AI inti sebagaimana ditetapkan pada PRD. 

---

# 4. Non-Functional Requirements

Karakteristik kualitas mengacu pada karakteristik ISO/IEC 25010 yang disebut dalam PRD, yaitu **Functional Suitability, Performance Efficiency, Usability, Reliability, Security, dan Maintainability**. 

| ID         | Kategori ISO/IEC 25010 | Metrik                                   | Target                                                                    | Kondisi Ukur                                                    |
| ---------- | ---------------------- | ---------------------------------------- | ------------------------------------------------------------------------- | --------------------------------------------------------------- |
| **NFR-01** | Functional Suitability | Akurasi prediksi AI                      | **≥ 77%**                                                                 | Pada data pengujian prototype                                   |
| **NFR-02** | Functional Suitability | F1-score                                 | Memadai                                                                   | Pada evaluasi kategori kedisiplinan                             |
| **NFR-03** | Performance Efficiency | Latensi prediksi AI                      | **[ASUMSI-07] ≤ 3 detik**                                                 | Saat satu prediksi dijalankan pada kondisi penggunaan prototype |
| **NFR-04** | Performance Efficiency | Kemampuan penggunaan lintas perangkat    | Seluruh fitur utama dapat digunakan                                       | Pada browser desktop dan smartphone                             |
| **NFR-05** | Usability              | Keberhasilan menemukan siswa berisiko    | **≥ 80% pengguna uji**                                                    | Dalam pengujian tugas pengguna                                  |
| **NFR-06** | Usability              | Persepsi kemudahan pemantauan            | **≥ 70% pengguna uji** menyatakan lebih mudah                             | Setelah penggunaan prototype                                    |
| **NFR-07** | Reliability            | Ketersediaan fungsi utama saat pengujian | Fitur utama berjalan sesuai kebutuhan                                     | Pengujian fungsional prototype                                  |
| **NFR-08** | Security               | Perlindungan akses terhadap data siswa   | Data hanya digunakan sesuai fungsi sistem                                 | Pengujian akses dan penggunaan sistem                           |
| **NFR-09** | Security               | Privasi data siswa                       | Data siswa tidak digunakan di luar kebutuhan sistem                       | Pemeriksaan penggunaan data                                     |
| **NFR-10** | Maintainability        | Kemudahan perubahan fitur prototype      | Fitur dapat diperbarui tanpa mengubah kebutuhan produk secara keseluruhan | Pemeriksaan saat pengembangan                                   |
| **NFR-11** | Functional Suitability | Cakupan rekomendasi intervensi           | **≥ 70% siswa berisiko** memiliki rekomendasi tindak lanjut               | Perbandingan siswa berisiko dengan rekomendasi yang tersedia    |

Target NFR-01, NFR-02, NFR-05, NFR-06, dan NFR-11 diturunkan langsung dari KPI PRD. 

**Catatan penting:** batas latensi AI, target reliabilitas numerik, dan metrik maintainability tidak diberikan dalam PRD. Karena format SRS meminta target pengukuran, nilai **≤ 3 detik pada NFR-03 merupakan [ASUMSI-07]**, bukan hasil riset. Target tersebut perlu divalidasi kembali sebelum ditetapkan sebagai persyaratan final.

---

# 5. Kebutuhan Data Minimum Fitur AI

PRD menyebut empat fitur yang paling berpengaruh terhadap kedisiplinan, yaitu **persentase absensi, jumlah alfa, keterlambatan, dan prestasi akademik**. 

### Input → Proses Prediksi → Output

| Bagian   | Kebutuhan                                              |
| -------- | ------------------------------------------------------ |
| Input 1  | Persentase kehadiran/absensi siswa                     |
| Input 2  | Jumlah alfa                                            |
| Input 3  | Jumlah keterlambatan                                   |
| Input 4  | Prestasi akademik/rata-rata nilai                      |
| Proses   | Klasifikasi tingkat kedisiplinan berdasarkan pola data |
| Output 1 | Kategori kedisiplinan: **tinggi / sedang / rendah**    |
| Output 2 | Skor risiko                                            |
| Output 3 | Rekomendasi intervensi                                 |

Data historis yang menjadi dasar penelitian berjumlah **711 siswa kelas X–XII dari 4 jurusan**. Model yang telah diuji mencakup Decision Tree, KNN, dan Naive Bayes, dengan akurasi terbaik yang dilaporkan sebesar **77,62% menggunakan Naive Bayes**. 

PRD tidak mendefinisikan jumlah record minimum per kelas, format file, periode pengambilan data, atau pembagian data latih dan data uji. Oleh sebab itu, aspek-aspek tersebut belum ditetapkan dalam SRS.

---

# 6. Aturan Bisnis Hasil Riset

| ID        | Aturan Bisnis                                                                                                              |
| --------- | -------------------------------------------------------------------------------------------------------------------------- |
| **BR-01** | Tingkat kedisiplinan direpresentasikan dalam tiga kategori: tinggi, sedang, dan rendah                                     |
| **BR-02** | Prediksi kedisiplinan menggunakan pola data absensi dan prestasi akademik                                                  |
| **BR-03** | Persentase absensi merupakan salah satu fitur penting dalam prediksi                                                       |
| **BR-04** | Jumlah alfa merupakan salah satu fitur penting dalam prediksi                                                              |
| **BR-05** | Keterlambatan merupakan salah satu fitur penting dalam prediksi                                                            |
| **BR-06** | Prestasi akademik merupakan salah satu fitur penting dalam prediksi                                                        |
| **BR-07** | Hasil AI digunakan untuk membantu pengambilan keputusan, bukan menggantikan keputusan guru                                 |
| **BR-08** | Rekomendasi intervensi merupakan bahan pertimbangan bagi guru                                                              |
| **BR-09** | Sistem tidak menentukan hukuman atau sanksi siswa secara otomatis                                                          |
| **BR-10** | Hasil model tidak boleh diposisikan sebagai diagnosis pasti terhadap perilaku siswa                                        |
| **BR-11** | Generalisasi hasil model ke sekolah lain tidak dianggap otomatis valid karena dataset penelitian berasal dari satu sekolah |

Aturan tersebut konsisten dengan batasan AI dan non-goals pada PRD. 

---

# 7. Matriks Traceability

| ID SRS      | Fitur/Bagian PRD Terkait                          |
| ----------- | ------------------------------------------------- |
| FR-01       | Dashboard monitoring                              |
| FR-02       | Data siswa                                        |
| FR-03       | Pemantauan absensi                                |
| FR-04       | Pemantauan absensi                                |
| FR-05       | Pemantauan absensi                                |
| FR-06       | Pemantauan prestasi akademik                      |
| FR-07 ★     | Prediksi tingkat kedisiplinan                     |
| FR-08 ★     | Skor risiko                                       |
| FR-09 ★     | Rekomendasi intervensi                            |
| FR-10       | Daftar prioritas siswa berisiko                   |
| FR-11       | Detail siswa                                      |
| FR-12       | Filter siswa                                      |
| FR-13       | Riwayat pemantauan                                |
| FR-14       | Tampilan mobile-responsive                        |
| FR-15       | Ringkasan kondisi kelas                           |
| FR-16       | Ringkasan untuk pimpinan                          |
| FR-17       | Notifikasi risiko                                 |
| NFR-01      | KPI akurasi prediksi ≥ 77%                        |
| NFR-02      | KPI F1-score                                      |
| NFR-03      | Kebutuhan latensi AI **[ASUMSI-07]**              |
| NFR-04      | Platform web + mobile-responsive                  |
| NFR-05      | KPI ≥ 80% pengguna mampu menemukan siswa berisiko |
| NFR-06      | KPI ≥ 70% pengguna merasa pemantauan lebih mudah  |
| NFR-07      | Karakteristik Reliability                         |
| NFR-08      | Karakteristik Security                            |
| NFR-09      | Karakteristik Security/privasi                    |
| NFR-10      | Karakteristik Maintainability                     |
| NFR-11      | KPI ≥ 70% siswa berisiko memiliki rekomendasi     |
| BR-01–BR-06 | Bukti riset tentang kategori dan fitur penting    |
| BR-07–BR-10 | Non-goals dan prinsip penggunaan AI               |
| BR-11       | Keterbatasan dataset satu sekolah                 |

Struktur kebutuhan dan traceability di atas mengikuti instruksi PRD yang mengharuskan setiap FR/NFR dapat ditelusuri ke kebutuhan produk dan tidak memasukkan kebutuhan baru tanpa dasar. 

### Batasan SRS

SRS ini **tidak menetapkan arsitektur sistem, rancangan database, API, algoritma implementasi, teknologi pemrograman, maupun rancangan antarmuka**, karena aspek tersebut berada pada HLD/LLD dan bukan kebutuhan yang ditentukan dalam PRD. 
