# TM-4: Dokumentasi Pengujian API Menggunakan HTTP Client

Dokumentasi ini mencatat hasil pengujian *endpoint* RESTful API yang dikembangkan menggunakan HTTP Client (PowerShell `Invoke-RestMethod` / `curl.exe` / Postman).

---

## 1. Alat Pengujian (HTTP Client)
Dalam praktikum ini, pengujian dilakukan dengan menggunakan **PowerShell HTTP Client (`Invoke-RestMethod`)** untuk mengirimkan permintaan HTTP (`GET`, `POST`, `PUT`, `DELETE`) dan mengevaluasi respons JSON dari server Express.

---

## 2. Hasil Pengujian Endpoint

### A. Pengujian Route Welcome (`GET /api/v1`)
Memastikan server API v1 telah berjalan dan siap menerima permintaan.
* **Method**: `GET`
* **URL**: `http://localhost:3000/api/v1`
* **Status**: `200 OK`
* **Bukti Pengujian**:
  ![GET Welcome](../p2/01-welcome.png)

---

### B. Pengujian Query Parameter (`GET /api/v1/jadwal?status=aktif`)
Menguji kemampuan filtering data jadwal berdasarkan status `aktif`.
* **Method**: `GET`
* **URL**: `http://localhost:3000/api/v1/jadwal?status=aktif`
* **Status**: `200 OK`
* **Bukti Pengujian**:
  ![GET Filter Query](../p2/02-filter-query.png)

---

### C. Pengujian Tambah Data (`POST /api/v1/jadwal`)
Menguji penambahan resource baru dengan mengirimkan JSON body.
* **Method**: `POST`
* **URL**: `http://localhost:3000/api/v1/jadwal`
* **Body (JSON)**: `{"mataKuliah": "Keamanan Aplikasi", "status": "aktif"}`
* **Status**: `201 Created`
* **Bukti Pengujian**:
  ![POST Jadwal](../p2/03-post-sukses.png)

---

### D. Pengujian Route Bersarang (`GET /api/v1/jadwal/1/peserta`)
Menguji pemanggilan data relasional (peserta yang terdaftar pada jadwal ID 1).
* **Method**: `GET`
* **URL**: `http://localhost:3000/api/v1/jadwal/1/peserta`
* **Status**: `200 OK`
* **Bukti Pengujian**:
  ![Nested GET Peserta](../p2/04-nested-get.png)

---

### E. Pengujian Kasus Error / Negatif (`GET /api/v1/salah-route`)
Memastikan middleware *404 Not Found* menangani route yang tidak terdaftar.
* **Method**: `GET`
* **URL**: `http://localhost:3000/api/v1/salah-route`
* **Status**: `404 Not Found`
* **Bukti Pengujian**:
  ![404 Error Handling](../p2/05-kasus-negatif.png)