# Design — TEBAK HARGA!

## Stack
Web artifact static, single-file client-side (index.html + styles.css + app.js
sesuai ARCHITECTURE.md §1): satu objek state, data harga terpisah dari logika,
fungsi render murni dari state, handler tipis, localStorage hanya lewat satu
modul store. Tanpa backend, tanpa login, tanpa database.

## Visual
Tema pasar tradisional hangat: krem, hijau daun, dan aksen merah cabai — tanpa
gradasi dekoratif. Mobile-first, kartu bahan besar di tengah, angka harga
ditampilkan besar. Ilustrasi tiap bahan: bentuk CSS/kode sederhana (bukan foto
berlisensi, bukan emoji sebagai label).

## Game loop
MENU -> PLAYING -> ROUND_RESULT -> (ulang sampai 10) -> GAME_OVER -> MENU.
Satu requestAnimationFrame tidak diperlukan (bukan game aksi); animasi reveal
cukup lewat transisi CSS + angka yang dihitung naik lewat timer.

## Interaksi
Input angka dengan inputmode decimal, tombol "Kunci Tebakan" besar, Enter juga
mengunci. Tombol "Ronde Berikutnya" / "Lihat Hasil" setelah reveal. Tombol
"Main Lagi" dan "Ke Menu" di layar akhir. Momen delight: reveal harga dengan
angka berjalan dari tebakan menuju harga acuan, plus warna dan label verdict
yang berubah sesuai kedekatan.
