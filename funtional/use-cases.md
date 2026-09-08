# Use Case & Acceptance Criteria DisiplinGuard

Dokumen berikut mengikuti format yang diminta dan dibatasi pada **fitur utama Must Have**, dengan fokus pada alur deteksi dini berbasis AI yang menjadi fungsi inti DisiplinGuard. User Stories yang menjadi dasar utamanya adalah **US-06, US-07, dan US-08**.

## 1. Use Case

### UC-01: Deteksi Dini Tingkat Kedisiplinan Siswa

| Elemen            | Detail                                                                                                                                             |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ID**            | UC-01                                                                                                                                              |
| **Nama Use Case** | Deteksi Dini Tingkat Kedisiplinan Siswa                                                                                                            |
| **Aktor Utama**   | Guru BK / Wali Kelas                                                                                                                               |
| **Tujuan**        | Mengidentifikasi tingkat kedisiplinan siswa berdasarkan pola absensi dan prestasi akademik serta memperoleh skor risiko dan rekomendasi intervensi |
| **Prioritas**     | Must Have                                                                                                                                          |
| **Keterlacakan**  | US-06, US-07, US-08; FR-07, FR-08, FR-09; NFR-01, NFR-02, NFR-11                                                                                   |

### Pre-kondisi

1. Pengguna merupakan Guru BK atau Wali Kelas.
2. Data siswa tersedia.
3. Data minimum untuk prediksi tersedia, yaitu:

   * persentase kehadiran
   * jumlah alfa
   * jumlah keterlambatan
   * prestasi akademik atau rata-rata nilai
4. Sistem dapat melakukan proses prediksi terhadap data siswa.

### Post-kondisi

**Kondisi berhasil:**

Sistem menghasilkan:

1. kategori tingkat kedisiplinan **tinggi, sedang, atau rendah**
2. skor risiko siswa
3. rekomendasi intervensi berdasarkan hasil prediksi

**Kondisi gagal/fallback:**

Sistem tidak menampilkan prediksi apabila data minimum tidak tersedia atau proses prediksi tidak dapat dilakukan. Sistem memberikan informasi bahwa data perlu dilengkapi atau prediksi belum dapat diberikan.

---

## Skenario Utama, Happy Flow

| Langkah | Aktor                                             | Sistem                                                                                                           |
| ------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| 1       | Guru BK/Wali Kelas membuka data seorang siswa     | Sistem menampilkan data siswa                                                                                    |
| 2       | Guru memilih fungsi prediksi kedisiplinan         | Sistem memeriksa ketersediaan data minimum                                                                       |
| 3       | Guru mengonfirmasi proses prediksi                | Sistem menggunakan persentase kehadiran, jumlah alfa, keterlambatan, dan prestasi akademik sebagai data prediksi |
| 4       | Menunggu hasil                                    | Sistem menghasilkan prediksi tingkat kedisiplinan dengan waktu proses **[ASUMSI-07] ≤ 3 detik**                  |
| 5       | Melihat hasil                                     | Sistem menampilkan kategori **tinggi/sedang/rendah**                                                             |
| 6       | Melihat hasil risiko                              | Sistem menampilkan skor risiko yang berkaitan dengan hasil prediksi                                              |
| 7       | Melihat rekomendasi                               | Sistem menampilkan rekomendasi intervensi berdasarkan kategori risiko                                            |
| 8       | Guru menggunakan hasil sebagai bahan pertimbangan | Sistem mempertahankan hasil sebagai informasi pendukung keputusan dan tidak menentukan sanksi secara otomatis    |

**Catatan:** batas waktu **≤ 3 detik** berasal dari NFR-03 pada SRS, tetapi statusnya masih **[ASUMSI-07]** karena PRD tidak menyediakan bukti empiris mengenai target latensi tersebut.

---

# 2. Acceptance Criteria

## Skenario 1: Prediksi berhasil

### AC-01: Prediksi tingkat kedisiplinan berhasil

**Given**

* data siswa tersedia
* persentase kehadiran, jumlah alfa, jumlah keterlambatan, dan prestasi akademik tersedia
* sistem dapat melakukan proses prediksi

**When**

* Guru BK atau Wali Kelas menjalankan prediksi untuk siswa tersebut

**Then**

* sistem menghasilkan tepat satu kategori kedisiplinan dari **tinggi, sedang, atau rendah**
* sistem menampilkan hasil prediksi dalam waktu **[ASUMSI-07] ≤ 3 detik**
* sistem menampilkan skor risiko
* sistem menampilkan rekomendasi intervensi
* hasil dapat digunakan sebagai bahan pertimbangan guru

Kriteria ini sesuai dengan kebutuhan FR-07, FR-08, dan FR-09 serta kebutuhan data AI pada SRS.  

---

## Skenario 2: Prediksi tidak dapat dilakukan

### AC-02: Data minimum tidak lengkap

**Given**

* Guru BK atau Wali Kelas memilih seorang siswa
* salah satu atau lebih data minimum prediksi, yaitu persentase kehadiran, jumlah alfa, keterlambatan, atau prestasi akademik tidak tersedia

**When**

* pengguna menjalankan fungsi prediksi

**Then**

* sistem **tidak menghasilkan kategori kedisiplinan**
* sistem **tidak menghasilkan skor risiko**
* sistem menampilkan informasi bahwa data yang diperlukan belum lengkap
* sistem meminta pengguna melengkapi data yang diperlukan sebelum prediksi dapat dilakukan

**Catatan:** perilaku fallback ketika data tidak lengkap merupakan konsekuensi logis dari persyaratan bahwa fitur AI membutuhkan empat input minimum. Pesan atau bentuk validasi spesifik **belum ditentukan dalam SRS**, sehingga tidak dibuat lebih detail di luar sumber. 

---

## Ringkasan Kriteria Uji

| ID    | Kondisi                                | Hasil yang Diharapkan                                                          | Status   |
| ----- | -------------------------------------- | ------------------------------------------------------------------------------ | -------- |
| AC-01 | Seluruh data minimum tersedia          | Kategori kedisiplinan + skor risiko + rekomendasi tampil ≤ [ASUMSI-07] 3 detik | Sukses   |
| AC-02 | Salah satu data minimum tidak tersedia | Prediksi tidak dijalankan dan pengguna mendapat informasi data belum lengkap   | Fallback |

### Hubungan Use Case dengan User Story

**US-06 → Prediksi tingkat kedisiplinan**
**US-07 → Skor risiko**
**US-08 → Rekomendasi intervensi**

Ketiganya memang merupakan fitur AI **Must Have** dalam SRS. 

Secara keseluruhan, use case ini menjaga batas penting DisiplinGuard: **AI memberikan indikasi dan rekomendasi, sedangkan keputusan intervensi tetap berada pada Guru BK atau Wali Kelas**. Hal tersebut juga konsisten dengan aturan bisnis bahwa hasil AI tidak menggantikan keputusan guru dan tidak digunakan untuk menentukan hukuman secara otomatis. 
