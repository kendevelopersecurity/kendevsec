# KENDEVSEC — Ultimate Cyber Digital Studio

Website responsif untuk layanan IT, konsultasi keamanan digital yang etis, dan social media growth. Desain menggabungkan cyber purple, electric blue, dan luxury dark UI dengan animasi latar, efek suara tombol opsional, serta pemutar DJ.

## Fitur
- Landing page responsif untuk HP Android, tablet, dan desktop.
- Katalog layanan dinamis: tambah/edit/hapus, kategori, ikon, harga, deskripsi, dan status tampil dari Admin Panel.
- Form order yang membuat ringkasan dan meneruskannya ke WhatsApp.
- Blog/artikel: tambah/edit/hapus, kategori, ringkasan, isi artikel, penulis, sampul emoji, status draf/publikasi.
- FAQ: CRUD dan toggle tampil.
- Testimoni: CRUD dan toggle tampil.
- Pengaturan brand, nomor WhatsApp, Instagram, slogan, hero copy, about copy, dan maintenance mode.
- Section Builder sederhana untuk blok konten tambahan berbasis teks.
- Firebase Authentication untuk login admin; Firestore untuk data.
- Firestore Security Rules membatasi perubahan data pada email admin yang ditentukan.
- Efek suara tombol hanya aktif jika pengunjung menyalakannya.
- Musik DJ melalui tombol play/pause. Browser Android umumnya memblokir autoplay bersuara; pengunjung harus mengetuk tombol play terlebih dahulu.

## File utama
- `index.html`, `styles.css`, `app.js`: website publik.
- `admin.html`, `admin.js`: Admin Panel.
- `firebase-config.js`: konfigurasi aplikasi web Firebase.
- `firestore.rules`: aturan akses Firestore.
- `assets/dj-intro.mp3`: musik yang diputar setelah interaksi pengguna.

## Setup Firebase (wajib agar Admin Panel aktif)
1. Buka https://console.firebase.google.com/ lalu buat project.
2. Tambahkan aplikasi Web dan salin konfigurasi SDK ke `firebase-config.js`. Ganti nilai `GANTI_...`; jangan memasukkan private service-account key.
3. Firebase Console → Authentication → Sign-in method → aktifkan Email/Password.
4. Authentication → Users → Add user: buat email dan password admin yang kuat.
5. Build → Firestore Database → Create database.
6. Edit `firestore.rules`, ganti `GANTI_DENGAN_EMAIL_ADMIN_ANDA` dengan email admin persis, lalu Publish pada tab Rules.
7. Untuk fitur gambar upload sungguhan, Firebase Storage dapat ditambahkan kemudian. Versi ini menggunakan emoji sampul agar bisa langsung dikelola tanpa upload file.
8. Authentication → Settings → Authorized domains: tambahkan domain GitHub Pages, misalnya `username.github.io`.

> Catatan: konfigurasi Firebase Web API key memang berada di frontend; keamanan harus ditegakkan dengan Authentication dan Firestore Rules. Jangan pernah menaruh service-account key atau password admin di source code.

## Deploy ke GitHub Pages lewat HP Android
1. Ekstrak ZIP ini.
2. Buat repository GitHub baru.
3. Upload **isi folder KENDEVSEC** ke root repository (pastikan `index.html` ada di root, bukan di dalam subfolder tambahan).
4. Repository → Settings → Pages → Deploy from a branch → branch `main` → folder `/(root)` → Save.
5. Tunggu deployment selesai. Pastikan file `assets/dj-intro.mp3` ikut terunggah.
6. Lengkapi setup Firebase di atas, kemudian buka `admin.html` dari domain Pages dan login.

## Penting untuk diketahui
- Admin Panel mengelola konten dan blok teks yang sudah didukung oleh CMS. Fitur aplikasi baru yang memerlukan logika khusus/API tetap membutuhkan pengembangan kode; Section Builder tidak menjalankan HTML atau JavaScript arbitrer demi keamanan.
- GitHub Pages adalah hosting statis. Data dinamis diambil dari Firestore; konten dapat gagal dimuat jika konfigurasi atau rules belum benar.
- Maintenance mode bergantung pada Firestore. Jika konfigurasi Firebase belum terpasang atau internet pengunjung putus, status maintenance tidak bisa diperiksa dari database.
- Sistem order membuka WhatsApp dengan pesan yang sudah disiapkan; website tidak memproses pembayaran otomatis.
- Gunakan audio publik hanya jika Anda memiliki hak/izin penggunaan yang diperlukan.
- Layanan keamanan siber hanya untuk sistem yang dimiliki atau dengan izin tertulis; jangan menawarkan akses ilegal, pencurian akun, atau serangan tanpa izin.

## Pemeriksaan paket
Paket ini ditujukan untuk hosting statis dan menggunakan modul JavaScript ES. Setelah konfigurasi Firebase dilakukan, uji login, simpan/edit/hapus tiap jenis konten, maintenance mode, order WhatsApp, dan pemutaran audio di perangkat target.
