# for you ♡ — Birthday Website

Website ucapan ulang tahun satu halaman: HTML + Tailwind CSS (CDN) + Vanilla JavaScript.
Tidak perlu install apa pun, tidak perlu build.

## Cara membuka

Klik dua kali `index.html`, atau buka di browser (Chrome, Edge, Safari, Firefox).
Butuh koneksi internet saat dibuka, karena Tailwind CSS dan Google Fonts dimuat dari CDN.

## 1. Ganti nama & tanggal

Buka `index.html`, cari bagian ini di dekat bagian bawah file (di dalam `<script>`):

```js
const birthdayData = {
  name: "HER NAME",
  birthday: "20 October 2026",
  age: 22,
  song: "assets/birthday-song.mp3"
};
```

- `name`: nama pacarmu. Otomatis muncul di hero, music player, final section, footer, dan judul tab browser.
- `birthday`: tulis dengan format `20 October 2026` (tanggal, nama bulan dalam bahasa Inggris, tahun).
  Format `20.10.2026` di bagian akhir dibuat otomatis dari sini.
- `age`: umur. `22nd` dibuat otomatis (21st, 23rd, dan seterusnya juga benar).
- `song`: path ke file lagu.

## 2. Tambahkan foto

Masukkan foto ke folder `images/` dengan nama persis seperti ini:

| File | Tempat muncul | Rasio yang disarankan |
|---|---|---|
| `memory-01.jpg` | Story: "The first hello" | portrait 4:5 |
| `memory-02.jpg` | Story: "The silly conversations" | portrait 3:4 |
| `memory-03.jpg` | Story: "The moments we didn't plan" | landscape 5:4 |
| `memory-04.jpg` | Story: "And everything in between" | portrait 4:5 |
| `photo-01.jpg` … `photo-05.jpg` | Memory Gallery | bebas (foto otomatis di-crop rapi) |

Kalau ada foto yang belum dimasukkan, akan muncul placeholder cream bertuliskan
*"your memory here"* beserta nama file yang dibutuhkan, jadi kamu tahu file mana yang belum ada.

Tips: kecilkan ukuran foto sampai lebar sekitar 1600px (±300–500 KB) supaya halaman tetap ringan.

## 3. Tambahkan lagu

Simpan lagu sebagai `assets/birthday-song.mp3`.
Lagu **tidak** diputar otomatis (browser memblokir autoplay). Lagu baru mulai ketika tombol Play ditekan.
Kalau file belum ada, player akan menampilkan catatan kecil yang memberi tahu file apa yang dibutuhkan.

## 4. Ubah teks

Semua teks (surat, wishes, caption foto, dan lainnya) ada langsung di `index.html`, per section:

- `#home`: hero
- `#intro`: "Today is about you."
- `#story`: 4 memory cards
- `#gallery`: galeri foto + caption saat di-hover
- `#message`: surat ulang tahun
- `#wishes`: 5 wishes (bisa diklik)
- `#listen`: music player
- `#final`: pesan penutup + tombol "Replay the story"

## Struktur

```
birthday/
├── index.html          ← semua kode (HTML, CSS, JS)
├── assets/
│   └── birthday-song.mp3
├── images/
│   ├── memory-01.jpg … memory-04.jpg
│   └── photo-01.jpg … photo-05.jpg
└── README.md
```

## Fitur

- Parallax 4 layer (blob → botanical → dekorasi kecil → konten) dengan `requestAnimationFrame`,
  dibuat lebih halus di tablet/mobile
- Scroll reveal dengan `IntersectionObserver` (800ms, `cubic-bezier(0.22, 1, 0.36, 1)`, stagger)
- Navbar sticky: transparan di atas, berubah jadi cream blur saat scroll, ada indikator section aktif
- Hamburger menu di mobile (bisa ditutup dengan Esc)
- Grid editorial: 12 kolom (desktop), 6 kolom (tablet), 1 kolom (mobile)
- Music player custom: play/pause, progress, waktu, volume/mute, piringan vinyl berputar
- Wishes interaktif dengan efek kelopak bunga kecil
- Cursor halus khusus desktop (tidak aktif di layar sentuh)
- Mendukung `prefers-reduced-motion`: parallax, animasi melayang, dan reveal dikurangi atau dimatikan
- Ilustrasi botanical semuanya SVG inline, tanpa gambar dari internet

## Membagikan sebagai link (opsional)

Drag-and-drop folder `birthday/` ke [Netlify Drop](https://app.netlify.com/drop), atau upload ke GitHub Pages.
Kamu akan dapat link yang bisa langsung dikirim.
