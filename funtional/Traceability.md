Berikut **Matriks Traceability DisiplinGuard** yang diturunkan dari FR pada SRS, User Story, UC-01, dan Acceptance Criteria yang diberikan. Untuk kebutuhan yang belum memiliki turunan lengkap sampai Acceptance Criteria atau Use Case formal, saya tandai **[BELUM LENGKAP]** sesuai aturan.

### Matriks Traceability

| ID Kebutuhan | ID User Story terkait | ID Use Case terkait | ID Acceptance Criteria terkait                 | Komponen Teknis & Model AI yang terlibat                          | Rencana Uji                                               |
| ------------ | --------------------- | ------------------- | ---------------------------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------- |
| **FR-01**    | US-14                 | **[BELUM LENGKAP]** | AC-US14-01, AC-US14-02, AC-US14-03             | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box, UAT, usability testing                         |
| **FR-02**    | US-01                 | **[BELUM LENGKAP]** | AC-US01-01, AC-US01-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box                                                 |
| **FR-03**    | US-02                 | **[BELUM LENGKAP]** | AC-US02-01, AC-US02-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box                                                 |
| **FR-04**    | US-03                 | **[BELUM LENGKAP]** | AC-US03-01, AC-US03-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Unit test, Black-box                                      |
| **FR-05**    | US-04                 | **[BELUM LENGKAP]** | AC-US04-01, AC-US04-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Unit test, Black-box                                      |
| **FR-06**    | US-05                 | **[BELUM LENGKAP]** | AC-US05-01, AC-US05-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box                                                 |
| **FR-07 ★**  | US-06 ★               | **UC-01**           | AC-US06-01, AC-US06-02, AC-US06-03, AC-US06-04 | **Model AI klasifikasi** sebagai aktor pendukung                  | Integration testing, Data evaluation, Performance testing |
| **FR-08 ★**  | US-07 ★               | **UC-01**           | AC-US07-01, AC-US07-02, AC-US07-03             | **Model AI klasifikasi** sebagai aktor pendukung                  | Integration testing, UAT                                  |
| **FR-09 ★**  | US-08 ★               | **UC-01**           | AC-US08-01, AC-US08-02, AC-US08-03, AC-US08-04 | **Model AI klasifikasi** sebagai aktor pendukung                  | Integration testing, Data evaluation, UAT                 |
| **FR-10**    | US-10                 | **[BELUM LENGKAP]** | AC-US10-01, AC-US10-02, AC-US10-03             | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box, UAT                                            |
| **FR-11**    | US-09                 | **[BELUM LENGKAP]** | AC-US09-01, AC-US09-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Inspection, UAT                                           |
| **FR-12**    | US-11                 | **[BELUM LENGKAP]** | AC-US11-01, AC-US11-02, AC-US11-03             | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Black-box                                                 |
| **FR-13**    | US-13                 | **[BELUM LENGKAP]** | AC-US13-01, AC-US13-02, AC-US13-03             | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | Integration testing, Black-box                            |
| **FR-14**    | US-12                 | **[BELUM LENGKAP]** | AC-US12-01, AC-US12-02                         | Tidak ada komponen teknis/model AI formal yang ditetapkan pada UC | UAT, Compatibility testing                                |
| **FR-15**    | **[BELUM LENGKAP]**   | **[BELUM LENGKAP]** | **[BELUM LENGKAP]**                            | Tidak ditentukan pada sumber                                      | **[BELUM LENGKAP]**                                       |
| **FR-16**    | **[BELUM LENGKAP]**   | **[BELUM LENGKAP]** | **[BELUM LENGKAP]**                            | Tidak ditentukan pada sumber                                      | **[BELUM LENGKAP]**                                       |
| **FR-17**    | **[BELUM LENGKAP]**   | **[BELUM LENGKAP]** | **[BELUM LENGKAP]**                            | Tidak ditentukan pada sumber                                      | **[BELUM LENGKAP]**                                       |

### Legenda ID Acceptance Criteria

| User Story | ID Acceptance Criteria | Skenario                                                    |
| ---------- | ---------------------- | ----------------------------------------------------------- |
| US-01      | AC-US01-01             | Data siswa tersedia                                         |
|            | AC-US01-02             | Data siswa tidak tersedia                                   |
| US-02      | AC-US02-01             | Persentase kehadiran tersedia                               |
|            | AC-US02-02             | Data absensi belum tersedia                                 |
| US-03      | AC-US03-01             | Jumlah alfa tersedia                                        |
|            | AC-US03-02             | Jumlah alfa bernilai nol                                    |
| US-04      | AC-US04-01             | Jumlah keterlambatan tersedia                               |
|            | AC-US04-02             | Jumlah keterlambatan bernilai nol                           |
| US-05      | AC-US05-01             | Prestasi akademik tersedia                                  |
|            | AC-US05-02             | Data prestasi akademik tidak tersedia                       |
| US-06 ★    | AC-US06-01             | Menghasilkan prediksi tingkat kedisiplinan                  |
|            | AC-US06-02             | Prediksi dengan kehadiran maksimal dan tanpa ketidakhadiran |
|            | AC-US06-03             | Prediksi melebihi batas waktu                               |
|            | AC-US06-04             | Evaluasi akurasi model memenuhi target ≥ 77%                |
| US-07 ★    | AC-US07-01             | Menampilkan skor risiko                                     |
|            | AC-US07-02             | Skor risiko tidak ditampilkan ketika prediksi gagal         |
|            | AC-US07-03             | Skor risiko tampil untuk mendukung pemantauan               |
| US-08 ★    | AC-US08-01             | Menampilkan rekomendasi intervensi                          |
|            | AC-US08-02             | Siswa berisiko memperoleh rekomendasi tindak lanjut         |
|            | AC-US08-03             | Minimal 70% siswa berisiko memiliki rekomendasi             |
|            | AC-US08-04             | Rekomendasi tidak ditampilkan tanpa hasil prediksi          |
| US-09      | AC-US09-01             | Faktor prediksi tersedia                                    |
|            | AC-US09-02             | Detail faktor tidak tersedia tanpa prediksi                 |
| US-10      | AC-US10-01             | Menampilkan daftar siswa berisiko                           |
|            | AC-US10-02             | Pengguna menemukan siswa berisiko ≥ 80%                     |
|            | AC-US10-03             | Daftar prioritas kosong                                     |
| US-11      | AC-US11-01             | Filter berdasarkan kelas                                    |
|            | AC-US11-02             | Filter berdasarkan jurusan                                  |
|            | AC-US11-03             | Filter menghasilkan data kosong                             |
| US-12      | AC-US12-01             | Mengakses fungsi utama melalui smartphone                   |
|            | AC-US12-02             | Melihat data siswa melalui smartphone                       |
| US-13      | AC-US13-01             | Menyimpan riwayat pemantauan                                |
|            | AC-US13-02             | Melihat riwayat pemantauan                                  |
|            | AC-US13-03             | Riwayat tidak berhasil disimpan                             |
| US-14      | AC-US14-01             | Menampilkan ringkasan kondisi kedisiplinan                  |
|            | AC-US14-02             | Menemukan siswa berisiko melalui dashboard ≥ 80%            |
|            | AC-US14-03             | Pemantauan dinilai lebih mudah ≥ 70%                        |

### Ringkasan Keterlacakan

Secara struktur, rantai yang **sudah lengkap** adalah:

**FR-07 → US-06 → UC-01 → AC-US06-01 s.d. AC-US06-04**

**FR-08 → US-07 → UC-01 → AC-US07-01 s.d. AC-US07-03**

**FR-09 → US-08 → UC-01 → AC-US08-01 s.d. AC-US08-04**

Ketiga FR tersebut merupakan inti fitur AI. UC-01 memang secara eksplisit mencakup **prediksi, skor risiko, dan rekomendasi intervensi**, dengan **Model AI klasifikasi** sebagai aktor pendukung.

Sementara itu, **FR-01 sampai FR-06 serta FR-10 sampai FR-14 sudah memiliki User Story dan Acceptance Criteria, tetapi belum memiliki Use Case formal yang menghubungkannya**. Karena aturan meminta traceability lengkap, kolom UC sengaja diberi **[BELUM LENGKAP]**, bukan dibuatkan UC baru secara diam-diam.

**FR-15, FR-16, dan FR-17 juga belum lengkap**, karena pada data yang diberikan belum terdapat User Story maupun Acceptance Criteria yang secara formal menurunkannya. Ini bagian yang paling jelas perlu dilanjutkan pada tahap requirements berikutnya.
