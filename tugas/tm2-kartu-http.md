# TM-2: Kartu HTTP (HTTP Method & Status Code)

Dokumen ini berisi penjelasan mengenai HTTP Methods dan Status Codes yang digunakan dalam pengembangan RESTful API pada praktikum backend Node.js dan Express.

---

## 1. HTTP Methods

| Method | Fungsi Utama | Sifat (Idempotent) | Contoh Penggunaan pada API |
| :--- | :--- | :--- | :--- |
| **GET** | Mengambil/membaca data dari server tanpa mengubah data di database. | Yes (Idempotent) | `GET /api/v1/jadwal` (Melihat daftar jadwal) |
| **POST** | Mengirimkan data baru ke server untuk disimpan. | No (Non-idempotent) | `POST /api/v1/jadwal` (Menambah jadwal baru) |
| **PUT** | Memperbarui/menggantikan data yang sudah ada berdasarkan identifier. | Yes (Idempotent) | `PUT /api/v1/jadwal/1` (Mengubah data jadwal ID 1) |
| **DELETE** | Menghapus data spesifik di server berdasarkan identifier. | Yes (Idempotent) | `DELETE /api/v1/jadwal/3` (Menghapus jadwal ID 3) |

---

## 2. HTTP Status Codes

### A. Success Responses (2xx)
* **`200 OK`**: Permintaan berhasil diproses oleh server. Digunakan pada method `GET`, `PUT`, dan `DELETE`.
* **`201 Created`**: Permintaan berhasil dan sumber daya (resource) baru telah dibuat. Digunakan pada method `POST`.

### B. Client Error Responses (4xx)
* **`400 Bad Request`**: Format permintaan tidak valid atau ada parameter/body wajib yang tidak dikirimkan oleh klien (misal: JSON rusak atau field `mataKuliah` kosong).
* **`404 Not Found`**: Endpoint URL atau data yang diminta tidak ditemukan di server (misal: `GET /api/v1/jadwal/99` saat ID 99 tidak ada).

### C. Server Error Responses (5xx)
* **`500 Internal Server Error`**: Terjadi kesalahan yang tidak terduga pada kode program atau server Express.