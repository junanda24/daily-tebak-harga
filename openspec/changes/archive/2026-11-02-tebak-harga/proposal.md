# Proposal — TEBAK HARGA! (2026-11-02)

## Apa
Game tebak harga sembako Indonesia: pemain menebak harga 10 bahan pokok per kilogram,
lalu melihat seberapa meleset tebakannya dari harga acuan nyata. Satu sesi selesai
dalam beberapa menit, bisa diulang dengan urutan acak.

## Kenapa mengejutkan
Semua orang belanja sembako, tapi hampir tidak ada yang hafal harganya per kilogram —
apalagi cabai rawit yang tembus Rp96 ribu. Game ini mengubah berita harga pangan yang
biasanya membosankan jadi taruhan harga yang bikin penasaran di tiap ronde:
"masa sih bawang semahal itu?" Efek kejutnya bukan gimmick visual, tapi datanya nyata.

## Kenapa bentuk game web (bukan package/CLI)
Kemarin (2026-11-01) sudah web app, tapi rotasi program menuntut variasi dan game
terakhir adalah 2026-10-29 — sudah 4 hari. Game HTML5 bisa langsung dimainkan di HP
tanpa install, dan mekanik tebak harga paling enak dimainkan lewat sentuhan, bukan CLI.

## Kenapa tanpa backend
Harga acuan adalah data statis tertanggal (PIHPS Nasional, Bank Indonesia,
per 1 November 2026). Tidak ada login, tidak ada data antar-pemain, skor hanya
localStorage di perangkat pemain. Backend hanya menambah beban tanpa manfaat.

## Data (sumber, bukan karangan)
Harga acuan = rata-rata nasional eceran PIHPS Nasional (Bank Indonesia) per
1 November 2026, dikutip dari pemberitaan 1 November 2026. Di dalam game wajib
tampil disclaimer: harga bisa berbeda per daerah dan pasar, dan angka ini adalah
acuan tanggal tersebut, bukan harga toko tertentu.

## IP check
Semua visual digambar lewat kode/CSS (ilustrasi sederhana per bahan). Tidak ada
foto, sprite, atau karakter berlisensi. Tidak ada disclaimer fan-made yang dibutuhkan.

## Anti-AI-slop
Copy Bahasa Indonesia natural, tanpa emoji di label, tanpa kata-kata generik
("selamat datang di dunia..."). Judul, label tombol, dan verdict ditulis seperti
orang pasar ngomong, singkat dan jelas.
