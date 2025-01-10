## **Laravel QR Code Generator**  

Aplikasi web untuk membuat QR code dari URL dengan fitur tambahan menambahkan gambar atau logo di tengah QR code. Tersedia dua opsi penggunaan: pembuatan QR code secara publik tanpa login dan pembuatan dengan login agar dapat menyimpan histori QR code yang dihasilkan.  

## **Fitur Utama:**  
- **Public QR Code Generation:**  
   - Pengguna dapat langsung membuat QR code tanpa login.  
   - Tidak menyimpan histori QR code yang dihasilkan.  
- **Private QR Code Generation (dengan login):**  
   - Pengguna perlu login untuk mengakses fitur ini.  
   - QR code yang dihasilkan akan disimpan dalam database.  
   - Tersedia fitur histori untuk melihat QR code yang pernah dibuat.  
- **Fitur Tambahan:**  
   - Input URL dan upload gambar untuk ditambahkan ke tengah QR code.  
   - Customisasi warna QR code (misal hitam putih atau warna custom).  
   - Pilihan ukuran QR code (small, medium, large).  
   - Download QR code sebagai file PNG.  
   - Validasi format URL dan gambar.  

## **Teknologi yang Digunakan:**  
- **Framework:** Laravel 11  
- **Library:**  
   - `simple-qrcode` untuk pembuatan QR code  
   - `intervention/image` untuk manipulasi gambar  
- **Database:** MySQL  
- **Frontend:** Blade dan Tailwind CSS (opsional)  
- **Deployment:** VPS dengan Ubuntu  

## **Alur Pengguna:**  
**Halaman Public Generation:**  
   - Pengguna membuka halaman utama.  
   - Memasukkan URL dan mengunggah gambar (opsional).  
   - Memilih warna dan ukuran QR code.  
   - Sistem menghasilkan QR code yang dapat langsung diunduh.  
   - QR code tidak disimpan dalam database.  

**Halaman Private Generation (Login):**  
   - Pengguna melakukan registrasi atau login.  
   - Memasukkan URL, mengunggah gambar, memilih warna dan ukuran QR code.  
   - QR code dihasilkan dan disimpan dalam database.  
   - Pengguna dapat mengunduh QR code dan melihat histori pembuatan.  

## **Model Data:**  
Tabel `admin`:  
- id  
- username  
- password  

Tabel `users`:  
- id  
- name  
- email  
- password  

Tabel `qr_codes`:  
- id  
- user_id (nullable untuk public generation)  
- url  
- image_path  
- qr_image_path  
- color  
- size  
- created_at  

## **Keamanan:**  
- Validasi URL, format gambar, warna, dan ukuran QR code.  
- Rate limiting pada public generation untuk mencegah penyalahgunaan.  
- Proteksi endpoint private dengan middleware autentikasi Laravel.  
- **Admin Management:**  
   - Hanya admin yang bisa menghapus data QR code di database.  
   - Endpoint admin dilindungi dengan autentikasi berbasis role.  

## **Pengembangan Bertahap:**  
- Public generation dengan validasi dasar.  
- Private generation dengan autentikasi dan penyimpanan data.  
- Customisasi warna dan ukuran QR code.  
- Manajemen admin untuk kontrol data.  
- Optimasi performa dan load balancing jika trafik tinggi.  
