# 🔗 Part 0: Menghubungkan HTML & CSS

Ada tiga cara untuk "menyuntikkan" gaya ke dalam HTML. Mari kita coba satu per satu.

### 1. External CSS (Cara Paling Direkomendasikan)

Ini adalah cara yang kita gunakan di Part 1-10. CSS ditulis di file terpisah (misal: `style.css`).

- **Kelebihan:** Kode rapi, satu file CSS bisa dipakai untuk banyak halaman HTML.
- **Cara:** Gunakan tag `<link>` di dalam bagian `<head>`.

```html
<head>
  <link rel="stylesheet" href="style.css" />
</head>
```

### 2. Internal CSS

CSS ditulis langsung di dalam file HTML, biasanya di bagian atas.

- **Kelebihan:** Praktis untuk halaman yang hanya satu (misal: landing page sederhana).
- **Cara:** Gunakan tag `<style>` di dalam `<head>`.

```html
<head>
  <style>
    body {
      background-color: linen;
    }
    h1 {
      color: maroon;
    }
  </style>
</head>
```

### 3. Inline CSS

CSS ditulis langsung di dalam atribut elemen HTML.

- **Kelebihan:** Sangat cepat untuk perbaikan kecil.
- **Kekurangan:** Membuat kode HTML kotor dan sulit diatur jika jumlahnya banyak.
- **Cara:** Gunakan atribut `style="..."`.

```html
<h1 style="color: blue; font-size: 20px;">Halo Dunia!</h1>
```

---

### 🛠️ Praktek: "The Connector Test"

Mari kita coba praktekkan ketiga cara ini sekaligus dalam satu file untuk melihat perbedaannya.

#### Langkah 1: Buat file `index.html`

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Uji Coba Penautan</title>

    <link rel="stylesheet" href="style.css" />

    <style>
      p {
        color: gray;
        font-family: sans-serif;
      }
      .box {
        width: 200px;
        height: 100px;
        background-color: lightblue;
        margin: 10px;
      }
    </style>
  </head>
  <body>
    <h1>Aku External/Internal?</h1>
    <p>Aku diatur oleh Internal CSS.</p>

    <div class="box" style="border: 5px solid navy;">
      Aku punya border dari Inline CSS!
    </div>
  </body>
</html>
```

#### Langkah 2: Buat file `style.css`

```css
/* Ini akan mewarnai h1 di file HTML tadi */
h1 {
  color: darkgreen;
  text-decoration: underline;
}
```

---

### 🔍 Analisis "Adu Kuat"

Ingat materi **Part 3 (Specificity)**? Jika ada aturan yang bertabrakan di ketiga cara ini, urutan kekuatannya adalah:

1. **Inline CSS** (Paling Kuat/Menang).
2. **Internal & External** (Sama kuat, yang menang adalah yang ditulis paling bawah di bagian `<head>`).

### 💡 Tantangan untuk Kamu

Coba buat sebuah paragraf baru. Beri warna merah menggunakan **Internal CSS**, lalu timpa warna tersebut menjadi biru menggunakan **Inline CSS**. Warna apa yang akhirnya muncul di browser? (Ini akan membuktikan siapa yang lebih kuat).

---

# 🎨 Part 1: Seni Menargetkan Elemen (The Art of Targeting)

Dalam CSS, sebelum kamu bisa mewarnai atau mengatur ukuran, kamu harus bisa "menunjuk" elemen mana yang ingin diubah. Di Part 1 ini, kita akan mempelajari 4 cara paling dasar untuk menunjuk elemen HTML.

### 📚 Teori Singkat

1. **Universal Selector (`*`)**: Seperti jaring raksasa yang menangkap **semua** elemen di halaman web tanpa terkecuali. Biasanya digunakan untuk "reset" margin dan padding bawaan browser.
2. **Type Selector**: Menunjuk elemen berdasarkan nama tag-nya (contoh: `h1`, `p`, `button`). Perubahan akan berdampak pada semua tag tersebut di seluruh halaman.
3. **Class Selector (`.nama-class`)**: Digunakan untuk mengelompokkan beberapa elemen agar memiliki gaya yang sama. Bisa dipakai berulang kali. Ditandai dengan titik (`.`) di CSS.
4. **ID Selector (`#nama-id`)**: Digunakan untuk elemen yang sangat spesifik dan **hanya ada satu** di halaman tersebut (seperti NIK di KTP). Ditandai dengan pagar (`#`) di CSS.

---

### 🛠️ Praktek: Membuat "Hero Section" Sederhana

Kita tidak hanya belajar teori. Mari kita langsung membuat bagian atas website (Hero Section). Ikuti langkah-langkah di bawah ini:

#### Langkah 1: Siapkan Struktur HTML

Buat file bernama `index.html` dan tempelkan kode ini:

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <link rel="stylesheet" href="style.css" />
    <title>Belajar CSS Part 1</title>
  </head>
  <body>
    <header id="main-header">
      <h1>Selamat Datang di Dunia CSS</h1>

      <p class="deskripsi-teks">
        Hari ini kita belajar cara menargetkan elemen dengan tepat.
      </p>

      <p class="deskripsi-teks">
        CSS membuat web yang membosankan jadi luar biasa.
      </p>

      <button>Mulai Belajar</button>
    </header>
  </body>
</html>
```

#### Langkah 2: Berikan Nyawa dengan CSS

Buat file bernama `style.css` di folder yang sama. Kita akan gunakan 4 jenis selector yang tadi dipelajari:

```css
/* 1. UNIVERSAL SELECTOR: Menghapus jarak bawaan browser agar rapi */
* {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}

/* 2. ID SELECTOR: Menata area header utama (Gunakan tanda #) */
#main-header {
  background-color: #2c3e50;
  color: white;
  padding: 50px;
  text-align: center;
}

/* 3. TYPE SELECTOR: Mengubah semua tag h1 (Gunakan nama tag langsung) */
h1 {
  font-size: 40px;
  margin-bottom: 20px;
}

/* 4. CLASS SELECTOR: Mengatur semua elemen dengan class 'deskripsi-teks' (Gunakan tanda titik .) */
.deskripsi-teks {
  color: #bdc3c7;
  font-style: italic;
  margin-bottom: 10px;
}

/* Bonus - Type Selector lagi untuk tombol */
button {
  padding: 10px 20px;
  cursor: pointer;
}
```

---

### 🔍 Analisis Hasil Praktek

Setelah kamu membuka `index.html` di browser, perhatikan hal berikut:

- **Universal Selector** memastikan tidak ada celah putih di pinggir halaman.
- **ID Selector** (`#main-header`) memberikan warna gelap hanya pada kotak header.
- **Type Selector** (`h1`) membuat judul menjadi besar.
- **Class Selector** (`.deskripsi-teks`) mengubah **kedua** paragraf secara bersamaan karena keduanya memiliki class yang sama.

### 💡 Tantangan untuk Kamu (Challenge)

Coba tambahkan satu tombol lagi di bawah tombol "Mulai Belajar" pada file HTML. Berikan class `.btn-secondary` pada tombol baru tersebut, lalu di file CSS, buatlah tombol tersebut berwarna latar kuning.

---

Mantap! Kamu sudah menguasai cara menembak elemen secara "langsung" di Part 1. Sekarang di **Part 2**, kita akan belajar cara menembak elemen berdasarkan **hubungannya** dengan elemen lain.

Di dunia CSS, ini disebut **Combinators**. Anggap saja ini seperti silsilah keluarga (Orang tua, Anak, Saudara).

---

# 🌳 Part 2: Silsilah Keluarga CSS (Combinators)

Kenapa ini penting? Karena seringkali kita tidak ingin memberi `class` pada setiap elemen HTML. Kita ingin bilang: _"Tolong warnai semua link yang ada di dalam kotak menu saja, jangan link yang lain."_

### 📚 Teori Singkat (4 Jurus Sakti)

1. **Descendant Selector (Spasi `     `)**: Menargetkan **semua keturunan** (anak, cucu, cicit) di dalam elemen tertentu.
2. **Child Selector (`>`)**: Menargetkan hanya **anak kandung** (elemen tepat di bawahnya). Cucu tidak ikut.
3. **Adjacent Sibling Selector (`+`)**: Menargetkan **satu adik tepat** di bawah elemen tersebut.
4. **General Sibling Selector (`~`)**: Menargetkan **semua adik** (saudara yang muncul setelahnya) yang berada di bawah induk yang sama.

---

### 🛠️ Praktek: Membuat "Article Card"

Kita akan membuat sebuah kartu artikel. Kita akan mengatur gayanya tanpa harus memberikan banyak class, cukup mengandalkan posisi mereka.

#### Langkah 1: Siapkan Struktur HTML

Ganti isi `index.html` kamu dengan kode ini:

```html
<div class="card">
  <h2>Judul Artikel Utama</h2>
  <p>Ini adalah paragraf pembuka (Anak kandung).</p>

  <div class="content-box">
    <p>Ini adalah paragraf di dalam box (Cucu).</p>
    <span>Catatan kecil di dalam box.</span>
  </div>

  <h3>Sub-judul Artikel</h3>
  <p>Paragraf setelah sub-judul 1.</p>
  <p>Paragraf setelah sub-judul 2.</p>
</div>
```

#### Langkah 2: Eksperimen dengan CSS

Gunakan `style.css` untuk melihat perbedaan cara kerja masing-masing selector:

```css
/* 1. DESCENDANT SELECTOR: Semua paragraf di dalam .card jadi abu-abu */
.card p {
  color: #555;
  line-height: 1.6;
}

/* 2. CHILD SELECTOR: Hanya paragraf anak kandung .card yang punya border bawah */
/* Paragraf "Cucu" di dalam .content-box TIDAK akan kena efek ini */
.card > p {
  border-bottom: 2px solid gold;
  padding-bottom: 5px;
}

/* 3. ADJACENT SIBLING: Cari <h3>, lalu beri warna biru hanya pada SATU paragraf tepat di bawahnya */
h3 + p {
  color: royalblue;
  font-weight: bold;
}

/* 4. GENERAL SIBLING: Semua span yang ada setelah .content-box akan miring */
/* (Walaupun di contoh ini cuma ada satu, ini berguna jika ada banyak elemen) */
.content-box ~ span {
  font-style: italic;
  background-color: #eee;
}
```

---

### 🔍 Mari Kita Bedah Hasilnya!

- Lihat paragraf di dalam `.content-box`. Dia berwarna abu-abu karena dia **keturunan** (Descendant) dari `.card`, tapi dia tidak punya border kuning karena dia bukan **anak langsung** (Child).
- Lihat paragraf di bawah `h3`. Hanya paragraf pertama yang berubah jadi biru tua. Paragraf kedua di bawahnya tetap abu-abu. Itulah kekuatan **Adjacent Sibling (`+`)**.

### 💡 Tantangan untuk Kamu (Challenge)

Coba tambahkan sebuah `<ul>` dengan beberapa `<li>` di dalam `.card`.

1. Gunakan **Child Selector** untuk membuat teks di dalam `<li>` berwarna merah.
2. Gunakan **Adjacent Sibling** untuk membuat `<li>` kedua memiliki margin kiri yang besar.

---

Siap, mari kita masuk ke **Part 3**. Kalau Part 1 dan 2 adalah cara "menembak" sasaran, Part 3 adalah tentang **"Siapa yang Paling Kuat"**.

Pernah tidak kamu sudah menulis CSS, tapi warnanya tidak berubah? Itu karena ada aturan **Cascade** dan **Specificity**. Anggap saja ini sebagai sistem kasta atau sistem poin di CSS.

---

# 🏆 Part 3: Kasta & Poin CSS (Cascade, Specificity, & Inheritance)

Di part ini, kita akan belajar kenapa sebuah kode bisa "menang" melawan kode lainnya.

### 📚 Teori Singkat

1. **Inheritance (Pewarisan)**: Beberapa properti (seperti `font-family` atau `color`) akan otomatis turun dari orang tua ke anak. Kamu tidak perlu mengatur font di setiap paragraf jika sudah mengaturnya di `body`.
2. **Aturan Terakhir (Order of Appearance)**: Jika dua selector punya kekuatan yang **sama**, maka kode yang ditulis **paling bawah (terakhir)** yang akan menang.
3. **Specificity (Tingkat Spesifik)**: Ini adalah sistem poin. Semakin spesifik caramu memanggil elemen, semakin kuat kodenya.

- **Level 1 (Type Selector)**: 1 Poin (lemah).
- **Level 2 (Class Selector)**: 10 Poin (sedang).
- **Level 3 (ID Selector)**: 100 Poin (sangat kuat).

---

### 🛠️ Praktek: "The Battle of Colors" (Pertempuran Warna)

Kita akan membuat satu elemen yang ditembak oleh banyak aturan sekaligus. Mari kita lihat siapa pemenangnya.

#### Langkah 1: Siapkan Struktur HTML

Ganti isi `index.html` kamu:

```html
<div class="kontainer-utama">
  <h2 id="judul-spesifik" class="judul-umum">Siapa Pemenang Warnaku?</h2>

  <p>Aku hanya paragraf biasa yang mewarisi gaya orang tuaku.</p>
</div>
```

#### Langkah 2: Eksperimen "Adu Mekanik" di CSS

Tulis kode ini di `style.css` secara berurutan:

```css
/* --- 1. CONTOH INHERITANCE --- */
.kontainer-utama {
  color: gray; /* Paragraf akan ikut jadi abu-abu tanpa disuruh */
  font-family: "Arial", sans-serif;
}

/* --- 2. CONTOH ORDER OF APPEARANCE --- */
/* Sama-sama Type Selector (1 poin). Yang bawah yang menang. */
h2 {
  color: red;
}
h2 {
  color: blue;
} /* Menang karena ditulis terakhir */

/* --- 3. CONTOH SPECIFICITY (ADU POIN) --- */

/* Skor: 1 (Type) */
h2 {
  color: orange;
}

/* Skor: 10 (Class) -> Mengalahkan Type */
.judul-umum {
  color: green;
}

/* Skor: 100 (ID) -> Mengalahkan Class & Type */
#judul-spesifik {
  color: purple;
}

/* Skor: 1 + 10 = 11 (Type + Class) -> Tetap kalah lawan ID */
div.judul-umum {
  text-decoration: underline;
}
```

---

### 🔍 Analisis Hasil Praktek

1. **Paragraf** jadi abu-abu karena **Inheritance** dari `.kontainer-utama`.
2. **H2** awalnya berwarna merah, lalu ditimpa biru (**Aturan Terakhir**).
3. Lalu, H2 berubah jadi hijau karena **Class** (10 poin) lebih kuat dari **Type** (1 poin).
4. Akhirnya, H2 akan berwarna **PURPLE** karena **ID** punya skor paling tinggi (100 poin). Tidak peduli seberapa banyak Class yang kamu tumpuk, satu ID biasanya akan selalu menang.

### 💡 Tantangan untuk Kamu (Challenge)

Coba tambahkan satu aturan lagi di paling bawah file CSS kamu:

1. Targetkan H2 tersebut menggunakan gabungan: `div h2#judul-spesifik`.
2. Berikan warna `gold`.
3. **Pertanyaan:** Apakah warnanya berubah jadi Gold? Hitung poinnya!

- `div` (1) + `h2` (1) + `#id` (100) = **102 poin**.

---

Siap! Kita masuk ke **Part 4**. Setelah tahu cara "menembak" dan "kasta" elemen, sekarang saatnya kita belajar mewarnai. Di CSS, warna bukan cuma soal `red` atau `blue`. Ada sistem yang jauh lebih presisi agar desainmu terlihat profesional.

---

# 🌈 Part 4: Dunia Warna & Transparansi (Color System)

Di part ini, kita akan belajar 4 cara memberikan warna dan bagaimana membuat efek transparan yang estetik.

### 📚 Teori Singkat

1. **Foreground Color (`color`)**: Digunakan untuk mewarnai **teks**.
2. **Background Color (`background-color`)**: Digunakan untuk mewarnai **latar belakang** kotak elemen.
3. **Sistem Warna**:

- **Color Name**: Nama standar (misal: `skyblue`, `tomato`). Terbatas hanya 140 warna.
- **HEX Code**: Kode 6 digit (misal: `#ff5733`). Paling sering digunakan desainer.
- **RGB (Red, Green, Blue)**: Menentukan intensitas cahaya merah, hijau, dan biru (0-255).
- **HSL (Hue, Saturation, Lightness)**:
- **Hue**: Warna pada lingkaran warna (0-360°).
- **Saturation**: Kepekatan warna (0-100%).
- **Lightness**: Terang/Gelap (0-100%).

4. **Alpha Channel (A)**: Menambahkan tingkat **transparansi** (0 = tembus pandang, 1 = solid). Digunakan pada `rgba` atau `hsla`.

---

### 🛠️ Praktek: Membuat "Glassmorphism Card"

Kita akan membuat kartu yang elegan dengan latar belakang transparan dan teks yang kontras.

#### Langkah 1: Siapkan Struktur HTML

Ganti isi `index.html` kamu:

```html
<div class="canvas">
  <div class="card-warna">
    <h2>Sistem Warna CSS</h2>
    <p>Belajar HEX, RGB, dan HSL untuk desain modern.</p>
    <div class="box-preview">Kotak Transparan</div>
  </div>
</div>
```

#### Langkah 2: Eksperimen Warna di CSS

Gunakan `style.css` untuk menerapkan berbagai sistem warna:

```css
/* Kita beri background pada canvas agar efek transparan terlihat */
.canvas {
  background-image: linear-gradient(45deg, #f39c12, #8e44ad);
  padding: 100px;
  height: 100vh;
}

.card-warna {
  /* 1. Menggunakan HEX untuk latar belakang putih */
  background-color: #ffffff;
  /* 2. Menggunakan RGB untuk warna teks utama */
  color: rgb(44, 62, 80);
  padding: 30px;
  border-radius: 15px;
  text-align: center;
}

h2 {
  /* 3. Menggunakan HSL: Warna Biru (200), Pekat (100%), Normal (50%) */
  color: hsl(200, 100%, 50%);
  margin-bottom: 20px;
}

.box-preview {
  margin-top: 20px;
  padding: 20px;
  /* 4. Menggunakan RGBA: Warna Hitam dengan Transparansi 0.1 (10%) */
  background-color: rgba(0, 0, 0, 0.1);
  /* 5. Menggunakan HSLA: Warna hijau transparan */
  border: 2px solid hsla(120, 100%, 25%, 0.5);
  color: #2ecc71;
  font-weight: bold;
}
```

---

### 🔍 Analisis Hasil Praktek

1. **Linear Gradient**: Kita menggunakan campuran dua warna HEX untuk latar belakang besar.
2. **RGBA vs RGB**: Perhatikan `.box-preview`. Karena kita pakai `rgba(0,0,0,0.1)`, warna latar belakang `canvas` (jingga/ungu) masih sedikit terlihat menembus kotak tersebut.
3. **HSL**: Sangat mudah mengubah warna biru menjadi merah hanya dengan mengganti angka `200` menjadi `0` atau `360` pada bagian **Hue**.

### 💡 Tantangan untuk Kamu (Challenge)

1. Coba ubah `background-color` pada `.card-warna` menjadi `hsla(0, 0%, 100%, 0.7)`.
2. Lihat apa yang terjadi! Kartu kamu sekarang akan terlihat seperti kaca (semi-transparan).
3. **Bonus**: Gunakan Google Search atau Color Picker untuk mencari kode HEX warna favoritmu dan terapkan pada teks `h2`.

---

Luar biasa! Kamu sudah bertahan sampai **Part 5**. Sekarang kita akan membahas cara membuat teks di websitemu tidak terlihat seperti dokumen Ms. Word tahun 90-an.

Setelah materi Part 5 ini selesai, kita akan melakukan **Mega Latihan** yang menggabungkan semua ilmu dari Part 1 sampai Part 5!

---

# ✍️ Part 5: Seni Menata Teks (Typography & Styling)

Tipografi adalah kunci utama kenyamanan membaca (User Experience) di sebuah website. Di part ini, kita akan membuat teks menjadi lebih hidup.

### 📚 Teori Singkat

1. **Font Basics**:

- `font-family`: Memilih jenis huruf (misal: 'Arial', 'Times New Roman', sans-serif).
- `font-size`: Ukuran huruf (biasanya menggunakan `px`, `em`, atau `rem`).
- `font-weight`: Ketebalan huruf (`normal`, `bold`, atau angka `100` - `900`).
- `font-style`: Biasanya untuk memiringkan teks (`italic`).

2. **Text Formatting**:

- `text-align`: Perataan teks (`left`, `center`, `right`, `justify`).
- `text-transform`: Mengubah kapitalisasi (`uppercase` untuk BESAR SEMUA, `lowercase`, `capitalize`).
- `text-decoration`: Biasanya untuk garis (`underline`, atau `none` untuk menghilangkan garis bawah pada link).

3. **Text Shadow**: Memberikan bayangan pada teks. Formatnya: `(geser-x) (geser-y) (blur) (warna)`.
4. **Elemen `<span>**`: Ini adalah tag HTML spesial. `<span>` digunakan untuk membungkus **satu kata atau bagian kecil** di dalam kalimat agar bisa kita beri gaya CSS tersendiri tanpa merusak baris paragraf.

---

# 🚀 MEGA LATIHAN: "Kartu Profil Estetik" (Gabungan Part 1 - 5)

Ini saatnya menguji semua yang telah kamu pelajari! Kita akan membuat sebuah Kartu Profil sederhana yang menggunakan:

- **Part 1**: ID, Class, Type, dan Universal Selector.
- **Part 2**: Descendant, Child, dan Adjacent Sibling Combinator.
- **Part 3**: Menang adu Specificity.
- **Part 4**: Penggunaan warna HEX, RGBA, dan HSL.
- **Part 5**: Tipografi, Text-shadow, dan `<span>`.

#### Langkah 1: Siapkan Struktur HTML

Ganti isi `index.html` kamu dengan kode ini:

```html
<div id="kartu-profil">
  <h1 class="nama-utama">Si <span>Paling</span> Koding</h1>

  <p class="jabatan">Tukang Sulap Website</p>

  <div class="bio-box">
    <p>Saya sedang belajar CSS dari nol.</p>
    <p>Ternyata CSS itu sangat <span>menyenangkan</span>!</p>
  </div>

  <h3>Senjata Rahasia</h3>
  <p>Daftar skill yang sedang dipelajari:</p>
  <ul>
    <li>HTML5</li>
    <li>CSS3</li>
  </ul>
</div>
```

#### Langkah 2: Terapkan CSS Gabungan

Hapus semua isi `style.css` kamu sebelumnya, lalu masukkan kode epik ini. Baca komentar di samping kodenya untuk mengingat materinya!

```css
/* =========================================
   PART 1 & 5: Universal & Font Family 
========================================= */
* {
  margin: 0;
  padding: 0;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

/* =========================================
   PART 1 & 4: ID Selector & Background HSL 
========================================= */
#kartu-profil {
  background-color: hsl(210, 20%, 95%); /* Abu-abu kebiruan terang */
  border-radius: 15px;
  padding: 40px;
  max-width: 400px;
  margin: 50px auto; /* Membuat kartu berada di tengah layar */
  text-align: center; /* Part 5: Semua teks di dalam rata tengah */
}

/* =========================================
   PART 1, 4 & 5: Class, HEX Color, Typography 
========================================= */
.nama-utama {
  color: #2c3e50; /* HEX Color gelap */
  font-size: 32px;
  text-transform: uppercase; /* Huruf BESAR semua */
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2); /* Part 4 & 5: Bayangan dengan RGBA (transparan) */
}

/* =========================================
   PART 5: Styling Span 
========================================= */
.nama-utama span {
  color: #e74c3c; /* Kata 'Paling' jadi merah */
  font-style: italic;
}

/* =========================================
   PART 2: Adjacent Sibling (+) 
========================================= */
h1 + p.jabatan {
  /* Menargetkan p.jabatan yang tepat berada di bawah h1 */
  color: #7f8c8d;
  font-weight: bold;
  margin-bottom: 20px;
  letter-spacing: 2px; /* Jarak antar huruf */
}

/* =========================================
   PART 2: Child Selector (>) & Descendant 
========================================= */
.bio-box {
  background-color: #ffffff;
  padding: 15px;
  border-left: 5px solid #3498db; /* Garis biru di kiri */
  margin-bottom: 20px;
  text-align: left; /* Mengesampingkan aturan center dari induknya */
}

/* Hanya paragraf anak langsung dari bio-box yang kena efek ini */
.bio-box > p {
  color: #34495e;
  line-height: 1.5; /* Jarak antar baris teks */
}

/* Span di manapun di dalam bio-box akan jadi tebal dan berwarna */
.bio-box span {
  font-weight: 900;
  color: #27ae60;
}

/* =========================================
   PART 3: Specificity War (Adu Poin) 
========================================= */
/* Aturan 1: Type selector (1 Poin) */
h3 {
  color: black;
}

/* Aturan 2: ID + Type (100 + 1 = 101 Poin) -> INI YANG MENANG! */
#kartu-profil h3 {
  color: #8e44ad; /* Ungu */
  text-decoration: underline; /* Part 5: Garis bawah */
  margin-bottom: 10px;
}

/* =========================================
   PART 2: General Sibling (~) 
========================================= */
/* Menargetkan semua ul yang posisinya setelah h3 */
h3 ~ ul {
  list-style-type: square; /* Mengubah buletan list jadi kotak */
  text-align: left;
  padding-left: 20px;
  color: #d35400; /* Warna oranye */
}
```

---

### 🔍 Cek Hasil Karya Kamu!

Buka di browser. Kamu seharusnya melihat sebuah kartu yang rapi di tengah layar.

- Judulnya besar, ada bayangannya, dan kata **"Paling"** berwarna merah miring (`<span>`).
- Tulisan "Tukang Sulap Website" punya jarak huruf yang lebar karena efek **Adjacent Sibling**.
- Kotak Bio berwarna putih dengan garis biru di kiri. Kata **"menyenangkan"** berwarna hijau tebal.
- Teks "Senjata Rahasia" berwarna ungu dan digarisbawahi karena berhasil menang **Specificity** menggunakan ID.
- Daftar list (HTML5 & CSS3) berikon kotak oranye berkat **General Sibling** dari `h3`.
