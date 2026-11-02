# TEBAK HARGA!

Game tebak harga sembako Indonesia: seberapa kenal kamu sama harga pasar?
Pemain menebak harga 10 bahan pokok per kilogram, lalu melihat seberapa meleset
tebakannya dari harga acuan nyata — satu sesi selesai dalam beberapa menit,
langsung bisa dimainkan di HP tanpa install.

## Kenapa ide ini dipilih

Semua orang belanja sembako, tapi hampir tidak ada yang hafal harganya per
kilogram — apalagi cabai rawit merah yang tembus Rp96.200. Game ini mengubah
berita harga pangan yang biasanya membosankan jadi taruhan harga yang bikin
penasaran di tiap ronde: "masa sih bawang semahal itu?" Efek kejutnya bukan
gimmick visual, tapi datanya nyata.

## Fitur

- 10 ronde per permainan, diacak dari 14 bahan pokok tanpa pengulangan
- Input tebakan Rupiah dengan keypad besar yang ramah sentuhan; Enter juga
  mengunci tebakan di desktop
- Validasi tebakan: kosong, nol, atau negatif ditolak dengan pesan jelas dan
  tetap di ronde yang sama
- Penilaian berdasarkan selisih persen: ≤5% = 100 poin ("Juragan Pasar!"),
  ≤10% = 80 ("Hampir Sempurna"), ≤20% = 60 ("Lumayan Dekat"),
  ≤35% = 30 ("Masih Jauh"), selebihnya = 10 ("Kebablasan")
- Bonus streak +20 bila tebakan ini dan sebelumnya sama-sama mendapat ≥60 poin
- Reveal harga dengan angka yang beranimasi dari tebakan menuju harga acuan,
  lengkap dengan selisih Rupiah dan selisih persen
- Layar akhir: total skor, gelar akhir (900+ "Juragan Pasar Sejati", 700+
  "Langganan Pasar", 450+ "Pembeli Rajin", selebihnya "Baru Pertama ke Pasar"),
  rekap 10 ronde, dan skor terbaik
- Skor terbaik tersimpan di localStorage perangkat pemain (hanya bila skor baru
  lebih besar)
- Tombol "Main Lagi" dan "Ke Menu" di layar akhir — tidak ada kondisi macet
- Ilustrasi tiap bahan digambar lewat kode/SVG, tanpa foto atau karakter
  berlisensi

## Cara main

1. Buka game, tekan "Mulai Main".
2. Lihat nama bahan dan satuannya (per kg), lalu ketik tebakan harga dalam
   Rupiah.
3. Tekan "Kunci Tebakan" (atau Enter) dan lihat harga acuannya.
4. Lanjutkan sampai 10 ronde, lalu lihat gelar akhirmu.
5. Tekan "Main Lagi" untuk ronde acak yang baru.

## Harga acuan (data, bukan karangan)

Harga acuan = rata-rata nasional eceran PIHPS Nasional (Bank Indonesia)
per 1 November 2026. Harga di tiap daerah dan pasar bisa berbeda; angka ini
adalah acuan tanggal tersebut, bukan harga toko tertentu.

| Bahan | Rp per kg |
|---|---:|
| Beras medium | 16.650 |
| Beras super | 18.000 |
| Telur ayam ras | 29.350 |
| Daging ayam ras | 39.000 |
| Daging sapi kualitas I | 152.700 |
| Minyak goreng curah | 20.350 |
| Minyak goreng kemasan bermerek I | 24.400 |
| Cabai rawit merah | 96.200 |
| Cabai merah besar | 71.600 |
| Cabai rawit hijau | 78.350 |
| Bawang merah | 37.100 |
| Bawang putih | 38.250 |
| Gula pasir premium | 20.600 |
| Gula pasir lokal | 19.500 |

## Cara menjalankan dari source

Tidak perlu build, tidak perlu server, tidak perlu backend:

```bash
# cukup buka file ini di browser
src/index.html
```

Atau jalankan server statis apa pun dari folder project, misalnya:

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000/src/
```

## Tech stack

- HTML, CSS, JavaScript murni (client-side saja, tanpa framework)
- Penyimpanan skor: localStorage (perangkat pemain saja)
- Tanpa backend, tanpa login, tanpa database

## Struktur folder

```
2026-11-02-tebak-harga/
├── README.md
├── src/
│   └── index.html        # game lengkap (hasil export artifact)
└── openspec/
    └── changes/
        └── archive/
            └── 2026-11-02-tebak-harga/
                ├── proposal.md
                ├── design.md
                ├── tasks.md
                └── specs/tebak-harga/spec.md
```

## Link hasil

- Game (artifact): `tebak-harga` (dibuka lewat kartu artifact di aplikasi Muse)
- Repo: https://github.com/junanda24/daily-tebak-harga
- Tanggal rilis: 2026-11-02

## Catatan saat build

- Keputusan penting: harga memakai satu tanggal acuan (1 November 2026) dan
  ditampilkan dengan disclaimer, bukan diklaim sebagai harga live atau harga
  toko tertentu — supaya game ini jujur, bukan sok akurat.
- Yang sengaja tidak dibuat: mode multiplayer dan harga live per kota.
  Keduanya butuh backend/data live dan akan merusak kesederhanaan game yang
  bisa selesai dalam beberapa menit.
- Verifikasi builder: alur penuh dimainkan lewat probe (mulai, tebakan kosong
  ditolak, tebakan Rp70.000 untuk cabai merah besar menghasilkan verdict
  "Juragan Pasar!" +100 poin, 10 ronde sampai layar akhir, skor terbaik
  tersimpan). Belum terverifikasi lewat probe: penguncian via Enter dan bonus
  streak +20 (logikanya sudah ditinjau di kode, belum sempat terjadi pada
  tebakan uji) — keduanya tercatat jujur di sini, bukan diklaim lolos probe.
