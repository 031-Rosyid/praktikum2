# TM-3: Analisis Perbandingan Paradigma API

Dokumen ini berisi analisis perbandingan 4 paradigma komunikasi API yang umum digunakan dalam pengembangan perangkat lunak modern.

---

## Tabel Perbandingan Paradigma API

| Fitur / Karakteristik | REST (Representational State Transfer) | GraphQL | gRPC | WebSocket |
| :--- | :--- | :--- | :--- | :--- |
| **Protokol Transport** | HTTP/1.1 atau HTTP/2 | HTTP/1.1 atau HTTP/2 | HTTP/2 | WebSocket Protocol (ws:// / wss://) |
| **Format Data** | JSON, XML, HTML | JSON | Protocol Buffers (Binary) | JSON, Text, Binary |
| **Model Komunikasi** | Request-Response (Stateless) | Request-Response (Single Endpoint) | Request-Response & Streaming | Bi-directional (Two-way Real-time Streaming) |
| **Skema / Kontrak** | OpenAPI / Swagger (Opsional) | GraphQL Schema (SDDL) | `.proto` File (Strict Schema) | Bebas / Tidak Terikat Skema Baku |
| **Kelebihan Utama** | Sederhana, universal, caching mudah. | Mencegah *over-fetching* & *under-fetching*. | Performa sangat tinggi, ukuran payload kecil. | Latensi sangat rendah untuk data *real-time*. |
| **Kekurangan Utama** | Risiko *over-fetching* data. | Kompleksitas query & caching di server lebih rumit. | Kurang ramah browser (butuh gRPC-Web). | Membutuhkan manajemen koneksi (stateful). |

---

## Ringkasan Penggunaan (Use Cases)

1. **REST API**: Cocok untuk aplikasi web/mobile umum (CRUD dasar), integrasi publik, dan sistem dengan kebutuhan caching tinggi.
2. **GraphQL**: Sangat baik untuk aplikasi dengan UI kompleks yang membutuhkan data dinamis dari berbagai resource dalam satu kali request.
3. **gRPC**: Ideal untuk komunikasi antar-layanan internal (*microservices*) yang membutuhkan kecepatan tinggi dan latensi rendah.
4. **WebSocket**: Tepat digunakan untuk fitur *real-time* seperti aplikasi obrolan (chat), notifikasi langsung, dasbor pemantauan, atau game *multiplayer*.