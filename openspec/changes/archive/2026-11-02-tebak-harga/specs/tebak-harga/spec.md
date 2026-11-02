# Spec — TEBAK HARGA!

## Data harga (Rp per kg, PIHPS Nasional 1 November 2026)
- Beras medium: 16650
- Beras super: 18000
- Telur ayam ras: 29350
- Daging ayam ras: 39000
- Daging sapi kualitas I: 152700
- Minyak goreng curah: 20350
- Minyak goreng kemasan bermerek I: 24400
- Cabai rawit merah: 96200
- Cabai merah besar: 71600
- Cabai rawit hijau: 78350
- Bawang merah: 37100
- Bawang putih: 38250
- Gula pasir premium: 20600
- Gula pasir lokal: 19500

## Requirements

### R1 — Layar mulai
- SHALL menampilkan judul TEBAK HARGA!, penjelasan singkat cara main, skor terbaik
  tersimpan (atau "belum ada" bila kosong), dan tombol mulai yang jelas.
- WHEN pemain menekan mulai THEN permainan dimulai di ronde 1 dari 10.

### R2 — Satu ronde
- SHALL menampilkan nama bahan, satuan "per kg", nomor ronde (x/10), skor berjalan,
  dan kolom tebakan angka (input + tombol cepat tambah/kurang tidak wajib, input
  angka wajib bisa diketik di HP).
- SHALL menolak tebakan kosong, nol, atau negatif dengan pesan yang jelas dan
  tetap di ronde yang sama.
- WHEN pemain mengunci tebakan THEN tampil hasil ronde itu sebelum lanjut.

### R3 — Penilaian
- SHALL menghitung selisih persen = |tebakan - harga acuan| / harga acuan.
- SHALL memberi poin: <=5% = 100 ("Juragan Pasar!"), <=10% = 80 ("Hampir Sempurna"),
  <=20% = 60 ("Lumayan Dekat"), <=35% = 30 ("Masih Jauh"), selain itu = 10
  ("Kebablasan").
- SHALL memberi bonus streak +20 bila tebakan ini dan sebelumnya sama-sama
  mendapat >=60 poin, dan menampilkannya sebagai bonus terpisah.
- SHALL menampilkan harga acuan, tebakan pemain, selisih rupiah, dan selisih persen.

### R4 — Akhir permainan
- SHALL setelah 10 ronde menampilkan total skor, gelar akhir (900+ "Juragan Pasar
  Sejati", 700+ "Langganan Pasar", 450+ "Pembeli Rajin", selain itu "Baru Pertama
  ke Pasar"), skor terbaik, dan tombol main lagi.
- SHALL menyimpan skor terbaik ke localStorage hanya bila skor baru lebih besar.
- SHALL selalu menyediakan jalan keluar: tombol main lagi dan kembali ke layar mulai,
  tidak ada kondisi macet (softlock).

### R5 — Pengalaman
- SHALL bisa dimainkan penuh lewat sentuhan di HP (tombol besar, input angka
  memunculkan keyboard numerik) dan keyboard di desktop (Enter mengunci tebakan).
- SHALL punya satu momen delight: animasi reveal harga (angka berjalan/terbuka)
  dan umpan balik visual berbeda untuk tebakan dekat vs jauh.
- SHALL menampilkan sumber dan disclaimer harga di layar mulai dan layar akhir.
- SHALL tanpa placeholder, tanpa fungsi mati, tanpa lorem ipsum.

## State (lima keranjang, ARCHITECTURE.md)
- Lokal: ronde berjalan, daftar acak 10 bahan, tebakan, skor, streak, fase
  (mulai/bermain/hasil-ronde/selesai). Tidak ada URL state, server state, global
  store, atau form library — ini game single-file client-side.
