# Jawaban Praktikum: Nela Noviyanti (10224170)

## Bagian 1: Pemanasan

**1. Anatomi aturan CSS**

Pada aturan `nav a.active:hover { color: red; }`:

- Selector: `nav a.active:hover`
- Deklarasi: `color: red;`
- Property: `color`
- Value: `red`
- Pseudo-class: `:hover`

**2. Elemen block dan inline**

- Block: `p`, `li`, `h2`
- Inline: `span`, `a`, `strong`

**3. Selector `.box p`**

Paragraf yang berwarna hijau adalah **A dan B**, karena keduanya merupakan elemen `<p>` yang berada di dalam elemen dengan class `box`. Paragraf C tidak terpilih karena class `box` dimiliki oleh paragraf itu sendiri, bukan elemen induknya. Paragraf D juga tidak terpilih karena berada di luar elemen `.box`.

**4. CSS specificity**

Warna teksnya adalah **merah**. Selector `#title` memiliki specificity lebih tinggi daripada selector `.heading` dan `h1`, sehingga deklarasi `color: red;` diterapkan.

**5. Kesalahan HTML**

Kesalahannya adalah urutan penutupan tag tidak sesuai dengan urutan pembukaan tag. Tag `<strong>` dibuka di dalam `<p>`, sehingga harus ditutup terlebih dahulu sebelum tag `<p>` ditutup.

Kode yang benar:

```html
<p>Hello <strong>world</strong></p>
```

## Bagian 3: Prediksi Selector Golf

**P1. Prediksi warna teks**

- (a) `Weekly hack nights.`: Hijau, karena cocok dengan selector `section p`.
- (b) `Bring your own laptop.`: Oranye, karena cocok dengan selector `.note` yang specificity-nya lebih tinggi daripada `section p`.
- (c) `© 2026 Student Affairs`: Biru, karena hanya cocok dengan selector `p`.

**P2. Urutan specificity tertinggi ke terendah**

1. `#tech p`
2. `.club p`
3. `main section p`
4. `p`

Alasannya, selector ID memiliki specificity lebih tinggi daripada class, sedangkan selector dengan elemen lebih banyak memiliki specificity lebih tinggi daripada selector dengan elemen lebih sedikit jika tidak ada ID atau class yang mengunggulinya.

**Setelah diuji (hasil sebenarnya):**

- (a) Hijau.
- (b) Oranye.
- (c) Biru.

Hasil pengujian sesuai dengan prediksi karena selector yang lebih spesifik mengalahkan selector yang specificity-nya lebih rendah.

## Bagian 4: Box model

**Q1 (content-box):**

Lebar yang terlihat dari tepi border ke tepi border adalah:

- Lebar content = 300 px
- Padding kiri dan kanan = 16 + 16 = 32 px
- Border kiri dan kanan = 1 + 1 = 2 px

Total lebar = 300 + 32 + 2 = **334 px**.

Margin 24 px di setiap sisi tidak dihitung karena margin berada di luar border.

**Q2 (border-box):**

Jika ditambahkan `box-sizing: border-box`, total lebar kartu termasuk padding dan border menjadi **300 px**. Lebar content menjadi 300 − 32 − 2 = **266 px**. Margin tetap berada di luar border.

**Pengecekan DevTools:**

Isi setelah memeriksa salah satu section di browser melalui DevTools → Computed → Box Model.

Content: 769.333 × 187.010 px
Padding: 16 px
Border: 0.667 px
Margin: 24 px atas dan bawah; 0 px kiri dan kanan

## Bagian 5: Tabel debug

### Bagian 5 — Debugging HTML dan CSS

| No. | Bug                                                                | Cara Menemukannya                          | Perbaikan                                             |
| --: | ------------------------------------------------------------------ | ------------------------------------------ | ----------------------------------------------------- |
|   1 | Properti `colour` tidak valid dalam CSS.                           | Membaca kode dan memeriksa DevTools.       | Mengubah `colour` menjadi `color`.                    |
|   2 | Deklarasi `background` tidak diakhiri titik koma.                  | Membaca kode CSS.                          | Menambahkan titik koma setelah `#dbe7f3`.             |
|   3 | Selector `.Card` tidak cocok dengan class `card` pada HTML.        | Memeriksa kecocokan selector dan class.    | Mengubah `.Card` menjadi `.card`.                     |
|   4 | Nilai `font-size: 18 px` memiliki spasi yang salah.                | Memeriksa deklarasi CSS.                   | Mengubahnya menjadi `font-size: 18px`.                |
|   5 | Nilai `centre` tidak valid untuk `text-align`.                     | Memeriksa properti CSS dan DevTools.       | Mengubah `centre` menjadi `center`.                   |
|   6 | Elemen `<h1>` ditutup dengan tag `</h2>`.                          | Membaca kode dan memeriksa validator HTML. | Mengganti `</h2>` menjadi `</h1>`.                    |
|   7 | Atribut `href` pada link About tidak memiliki tanda kutip penutup. | Membaca kode dan memeriksa validator HTML. | Mengubahnya menjadi `<a href="about.html">About</a>`. |
|   8 | ID pada HTML, `newsList`, berbeda dari selector CSS, `#news-list`. | Membandingkan selector CSS dengan ID HTML. | Menyamakan keduanya menjadi `news-list`.              |
|   9 | Elemen `<img>` tidak memiliki atribut `alt`.                       | Memeriksa kode dan validator HTML.         | Menambahkan `alt` yang menjelaskan gambar.            |

## Bagian 6: Tabel Code Review

| #   | Baris            | Masalah                                                               | Mengapa penting                                                                        | Perbaikan saya                                                     |
| --- | ---------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| 1   | Awal dokumen     | Tidak ada `<!DOCTYPE html>`                                           | Browser dapat menggunakan mode rendering yang tidak diharapkan                         | Tambahkan `<!DOCTYPE html>`                                        |
| 2   | Elemen `<html>`  | Tidak ada atribut `lang`                                              | Membantu teknologi bantu mengenali bahasa halaman                                      | Tambahkan `lang="en"` atau bahasa sesuai isi halaman               |
| 3   | Elemen `<head>`  | Tidak ada meta charset dan viewport                                   | Encoding dan tampilan responsif tidak dinyatakan dengan baik                           | Tambahkan meta charset dan viewport                                |
| 4   | `.header`        | Lebar tetap `1200px`                                                  | Halaman dapat melampaui layar perangkat kecil                                          | Gunakan `max-width` dan lebar yang responsif                       |
| 5   | `.nav a`         | Menggunakan `!important`                                              | Membuat aturan CSS lebih sulit dipelihara dan ditimpa                                  | Gunakan selector dan specificity yang sesuai                       |
| 6   | `.content`       | Warna teks `#bbbbbb` pada latar putih memiliki kontras rendah         | Teks menjadi sulit dibaca                                                              | Gunakan warna teks dengan kontras memadai                          |
| 7   | `.sidebar`       | Aturan CSS tidak digunakan                                            | Menambah kode yang tidak diperlukan                                                    | Hapus aturan yang tidak digunakan                                  |
| 8   | Struktur halaman | Menggunakan banyak `<div>` untuk bagian semantik                      | Struktur dan makna konten kurang jelas                                                 | Gunakan `<header>`, `<nav>`, `<main>`, `<section>`, dan `<footer>` |
| 9   | Judul kampus     | Nama kampus menggunakan `<div>` dan `<b>`                             | Tidak memberikan struktur heading yang semantik                                        | Gunakan `<h1>`                                                     |
| 10  | Judul bagian     | About Us dan Contact Us menggunakan `<div>`                           | Judul bagian tidak ditandai sebagai heading                                            | Gunakan `<h2>`                                                     |
| 11  | Isi halaman      | Menggunakan `<br>` berulang untuk mengatur jarak                      | Jarak seharusnya diatur menggunakan CSS                                                | Gunakan elemen paragraf dan margin CSS                             |
| 12  | Paragraf konten  | Teks deskripsi dibungkus `<div>`                                      | Tidak menunjukkan bahwa konten merupakan paragraf                                      | Gunakan `<p>`                                                      |
| 13  | Gambar           | Tidak memiliki atribut `alt`                                          | Pengguna pembaca layar tidak memperoleh deskripsi gambar                               | Tambahkan `alt` yang bermakna                                      |
| 14  | Formulir         | Input tidak memiliki `<label>`                                        | Pengguna mungkin kesulitan mengetahui tujuan setiap input                              | Tambahkan label dengan atribut `for` dan ID input yang sesuai      |
| 15  | Input email      | Email menggunakan `type="text"`                                       | Tidak memberikan validasi dasar untuk alamat email                                     | Gunakan `type="email"`                                             |
| 16  | Tombol           | Menggunakan JavaScript inline `onclick` hanya untuk menampilkan pesan | Perilaku dan struktur tidak dipisahkan dengan baik, dan tombol tidak mengirim formulir | Gunakan formulir dengan tombol submit dan penanganan yang sesuai   |
| 17  | Layout           | Menggunakan `float` untuk sidebar                                     | Layout lebih sulit dikelola dan disesuaikan pada layar kecil                           | Gunakan Flexbox atau Grid bila sesuai                              |
| 18  | Footer           | Menggunakan class `.footer` tanpa elemen semantik `<footer>`          | Struktur halaman kurang bermakna                                                       | Gunakan elemen `<footer>`                                          |

**Refleksi**

1. Masalah yang paling sulit disadari hanya dengan melihat halaman di browser adalah masalah semantik, aksesibilitas, dan struktur dokumen. Halaman bisa terlihat baik, tetapi penggunaan heading, label formulir, dan atribut gambar yang tidak tepat dapat mengurangi aksesibilitas.

2. Masalah tersebut tetap penting karena halaman web tidak hanya harus terlihat baik, tetapi juga harus valid, mudah diakses, responsif, dan mudah dipelihara. Struktur HTML yang baik juga membantu teknologi bantu dan mesin pencari memahami isi halaman.

3. Saya akan memeriksa struktur HTML, konsistensi selector CSS, aksesibilitas, dan tampilan responsif sebelum mengumpulkan tugas. Saya juga akan menggunakan W3C Validator serta DevTools untuk menemukan kesalahan yang tidak terlihat langsung di browser.

## Bagian 7: Exit ticket

**1. Jelaskan anatomi sebuah aturan CSS dengan kata-katamu sendiri.**

Aturan CSS terdiri dari selector dan blok deklarasi. Selector menentukan elemen HTML yang akan diberi gaya, sedangkan deklarasi terdiri dari property dan value yang menentukan gaya tersebut.

**2. Selector atau konsep apa dari hari ini yang masih membingungkan bagimu?**

Saya masih perlu berlatih membedakan specificity selector CSS, terutama ketika beberapa selector menargetkan elemen yang sama. Saya akan mencoba beberapa contoh dan memeriksa hasilnya melalui DevTools.

**3. Satu hal apa yang sekarang bisa kamu lakukan tanpa perlu mencarinya?**

Saya sekarang bisa membuat struktur HTML semantik dasar, menghubungkan file CSS eksternal, serta menggunakan selector sederhana untuk mengatur tampilan halaman web.
