3 GARAGE — PAKET WEBSITE + ADMIN CMS (TANPA FIREBASE)

ISI PAKET
- index.html, styles.css, app.js: website publik.
- admin.html, admin.js: panel admin.
- worker.js: backend Cloudflare Worker untuk login aman dan menyimpan konten ke GitHub.
- content/data.json: data awal katalog dan pengaturan.

PENTING
GitHub Pages tidak dapat menjalankan backend atau melindungi password. Jangan menghapus Worker.
Jangan pernah menaruh GitHub Personal Access Token di index.html, app.js, admin.html, atau admin.js.
Password awal yang diminta pemilik: username 10262026, password 3333. Karena password ini lemah, ganti ke password yang lebih kuat sebelum website dibuka publik.

LANGKAH A — UPLOAD KE GITHUB
1. Buka repository GitHub kamu.
2. Upload semua file/folder dari paket ini ke root repository. Pastikan index.html berada di root.
3. Commit changes.
4. Buka Settings > Pages > Build and deployment. Pilih Deploy from a branch, branch main, folder /(root), lalu Save.
5. Tunggu proses Pages selesai.

LANGKAH B — BUAT GITHUB TOKEN
1. GitHub > Settings > Developer settings > Personal access tokens > Fine-grained tokens.
2. Generate new token. Pilih repository 3-garage saja.
3. Repository permissions: Contents = Read and write. Buat token dan salin sementara. Jangan kirim token ke siapa pun.

LANGKAH C — CLOUDFLARE WORKER
1. Masuk Cloudflare, Workers & Pages, Create application, Create Worker.
2. Beri nama misalnya 3-garage-api, lalu Deploy.
3. Buka Edit code, ganti seluruh isi dengan worker.js dari paket ini, Save and deploy.
4. Di Worker > Settings > Variables and Secrets, tambahkan:
   ADMIN_USERNAME = 10262026
   ADMIN_PASSWORD = 3333 (disarankan ganti yang kuat)
   SESSION_SECRET = buat string acak panjang minimal 32 karakter
   GITHUB_OWNER = username GitHub kamu
   GITHUB_REPO = 3-garage (sesuaikan nama repository)
   GITHUB_BRANCH = main
   GITHUB_TOKEN = token GitHub tadi (Secret)
   SITE_ORIGIN = URL GitHub Pages kamu, contoh https://username.github.io
5. Pastikan GITHUB_TOKEN ditandai Secret. Deploy ulang jika diminta.

LANGKAH D — HUBUNGKAN WEBSITE KE WORKER
1. Setelah Worker aktif, salin URL Worker, biasanya https://nama-worker.username.workers.dev
2. Buka app.js dan admin.js di GitHub.
3. Ganti PASTE_CLOUDFLARE_WORKER_URL_HERE pada kedua file dengan URL Worker kamu. Jangan tambahkan slash di akhir.
4. Commit changes.

LANGKAH E — CEK
1. Buka URL website GitHub Pages.
2. Buka /admin.html untuk panel admin.
3. Login dengan username dan password yang kamu atur di Worker.
4. Ubah teks atau tambah produk, lalu Save & Publish.
5. Cek website publik. Perubahan mungkin butuh sedikit waktu sampai GitHub Pages selesai deploy.

CATATAN
- Foto produk pada versi ini memakai URL gambar publik; unggah foto ke layanan hosting gambar tepercaya lalu masukkan URL-nya.
- Booking mengirim detail melalui WhatsApp.
- Link admin tidak ditampilkan di menu utama; alamat panel adalah /admin.html.
- Website ini bukan toko dengan pembayaran online. Pesanan dikonfirmasi melalui WhatsApp.
