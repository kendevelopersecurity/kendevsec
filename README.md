# KENDEVSEC — Creative Marketplace Ultimate

Template baru dengan identitas **Creative Marketplace**: ivory, coral, pastel lavender, dan sage. Tidak memakai tampilan cyber gelap/neon dari versi sebelumnya.

## Isi paket
- `index.html`: halaman publik responsive, katalog layanan, artikel, FAQ, testimoni, form order, WhatsApp, tombol efek suara, dan pemutar DJ opsional.
- `admin.html`: dashboard admin dengan modul pengaturan website, layanan, artikel, FAQ, testimoni, section builder, pesanan, metadata role admin, audit log, dan ekspor CSV.
- `app.js`, `admin.js`, `styles.css`: logika dan tampilan.
- `firebase-config.js`: tempat konfigurasi Firebase project BARU.
- `firestore.rules`: contoh rules dengan placeholder email admin.
- `assets/dj-intro.mp3`: file musik yang disertakan.

## Sebelum dipublikasikan
1. Buat repository GitHub baru bernama `kendevsec` agar website lama tidak berubah.
2. Buat Firebase project baru khusus KENDEVSEC.
3. Isi nilai asli dari Firebase Console ke `firebase-config.js`. Jangan pernah memasukkan service-account/private key ke frontend.
4. Aktifkan Authentication → Sign-in method → Email/Password. Buat user admin di Authentication → Users.
5. Ganti `GANTI_DENGAN_EMAIL_ADMIN_ANDA` di `firestore.rules` dengan email admin yang tepat, lalu publish rules.
6. Buat database Firestore. Terapkan rules setelah memeriksa semua kebutuhan aplikasi.
7. Tambahkan domain GitHub Pages ke Firebase Authentication → Settings → Authorized domains.
8. Upload isi folder ini ke repository baru. Di Settings → Pages, pilih Deploy from a branch dan branch `main` / root.

## Catatan penting keamanan dan fungsi
- Konfigurasi Firebase masih placeholder; login dan database belum bisa aktif sebelum kamu memasukkan konfigurasi project sendiri.
- Order akan mencoba menyimpan ke koleksi `orders` jika Firebase sudah terkonfigurasi, lalu mengarahkan pelanggan ke WhatsApp. Jika Firestore belum aktif/izin ditolak, WhatsApp tetap dibuka tetapi order tidak tercatat di database.
- Role di `adminUsers` adalah metadata antarmuka; itu bukan pengganti custom claims atau aturan otorisasi produksi. Rules contoh membatasi admin dengan email tertentu. Jika ingin multi-role dengan izin berbeda yang benar-benar enforced, rules dan strategi custom claims perlu disiapkan dan diuji sebelum data pelanggan produksi digunakan.
- Firebase Storage belum dihubungkan ke upload gambar; saat ini kolom gambar belum melakukan upload ke cloud.
- GitHub Pages adalah hosting statis; maintenance mode bekerja melalui pengaturan Firestore saat situs dapat membaca Firebase.
- Browser mobile dapat memblokir autoplay audio. Pengguna harus menekan tombol DJ Play terlebih dahulu.
- Audit log di panel adalah best-effort; Firebase Rules dapat menolak penulisan jika email admin belum disetel benar.
- Uji di staging sebelum digunakan untuk transaksi nyata.

## Kontak brand (silakan verifikasi sebelum publikasi)
- WhatsApp: `62895636069948`
- Instagram: `@kendevsec`
- Email yang pernah dicantumkan pada konfigurasi proyek: `kendevelopersecurity@gmail.com`
