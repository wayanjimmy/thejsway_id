# Fungsi

## Pengenalan

Berikut adalah algoritma memasak mie instant.

```text
Begin
    Siapkan 1 bungkus mie instant, 2 gelas air, panci, mangkok dan garpu
    Masukan 2 gelas air kedalam panci
    Tunggu hingga mendidih
    Masukan mie ke dalam panci
    Tunggu dan aduk selama 3 menit
    Jika mie matang
        Masukan bumbu
    Aduk hingga rata
End
```

Berikut adalah algoritma yang sama namun ditulis dengan cara yang berbeda.

```text
Begin
    Masak air
    Masak mie
End
```

Cara pertama menjelaskan secara detil masing-masing langkah. Cara kedua memecah beberapa langkah menjadi cara yang umum dan memperkenalkan konsep re-useable dalam hal ini adalah Masak (Masak air & Masak mie).

## Mengenal fungsi lebih dalam

**Fungsi** adalah kumpulan beberapa statement yang mengerjakan sesuatu.

Ini adalah sebuah contoh fungsi.

```js
function menyapa() {
  console.log("Halo");
}

console.log("Program dimulai");
menyapa();
console.log("Program selesai");
```

### Deklarasi fungsi

### Memanggil fungsi

Fungsi harus dipanggil untuk dijalankan. Berikut adalah bagian kedua dari contoh program.

```js
console.log("Program dimulai");
menyapa();
console.log("Program selesai");
```

Baris pertama dan terakhir menampilkan pesan di layar. Baris kedua melakukan pemanggilan fungsi `menyapa()`.

Anda dapat memanggil fungsi dengan menuliskan nama fungsi diikuti sepasang tanda kurung.

```js
// ...
sebuahFungsi(); // Memanggil fungsi bernama sebuahFungsi
// ...
```

![Mekanisme pemanggilan fungsi](images/chapter05-02.png)

### Manfaat menggunakan fungsi

Masalah yang kompleks umumnya lebih mudah ditangani ketika dipecah menjadi beberapa masalah yang lebih sederhana. Program komputer, ditulis sebagai kombinasi dari beberapa fungsi singkat dan terfokus, program akan lebih mudah dipahami dan diperbarui daripada yang monolitik. Sebagai bonus tambahan, beberapa fungsi dapat digunakan kembali di program lain!

Membuat fungsi juga bisa menjadi solusi untuk masalah duplikasi kode, Daripada kode diduplikasi di beberapa tempat, sepotong kode yang dijadikan fungsi dapat dipanggil dari mana saja ketika diperlukan.

## Isi Fungsi

### Nilai kembali

Berikut adalah variasi dari program diatas.

```js
function menyapa() {
  return 'Halo';
}

console.log("Program dimulai");
const pesan = menyapa();  // Simpan nilai kembali dari fungsi di sebuah variabel 
console.log(pesan); // Tampilkan nilai kembali
console.log("Program selesai");
```

Jalankan kode diatas dan hasilnya akan sama saja.

Dalam contoh ini isi dari fungsi `menyapa` berbeda yang awalnya menggunakan `console.log('Halo');` diubah menjadi `return 'Halo';`.

Kata kunci `return` digunakan agar fungsi mengirim nilai kembali. Nilai kembali yang dikirim diletakan disetelah kata `return`.

```js
// Deklarasi sebuahFungsi
function sebuahFungsi() {
  let nilaiKembali;
  // Kalkulasi nilai kembali
  // nilaiKembali = ...
  return nilaiKembali;
}

// Mendapatkan nilai kembali dari memanggil sebuahFungsi
const hasil = sebuahFungsi();
// ...
```

Nilai kembali bisa bernilai apa saja (number, string, dll). Namun sebuah fungsi hanya bisa mengembalikan 1 nilai.

Jika Anda mencoba mengambil nilai kembali dari fungsi yang tidak mengembalikan nilai, makanya nilai yang didapat adalah `undefined`

```js
function fungsiSaya() {
  // ...
  // Tidak ada nilai kembali
}

const hasil = fungsiSaya();
console.log(hasil); // undefined
```

> Sebuah fungsi berhenti setelah statement return di eksekusi, baris kode dibawah return tidak akan dieksekusi

### Variabel lokal

Anda dapet mendeklarasi variabel dalam fungsi

```js
function menyapa() {
  const pesan = "Halo!";
  return pesan;
}

console.log(menyapa()); // "Halo!"
```

Fungsi `menyapa()` mendeklarasikan variabel bernama `pesan` dan mengembalikan nilainya dengan `return`.

Variabel yang berada didalam fungsi dinamakan variabel lokal, karena scope variabel tersebut hanya didalam fungsi. Diluar fungsi Anda tidak dapat mengaksesnya.

```js
function menyapa() {
  const pesan = "Halo!";
  return pesan;
}

console.log(menyapa()); // "Halo!"
console.log(pesan); // Error
```

Tidak dapat menggunakan variabel lokal diluar fungsi bukanlah hal yang buruk, justru hal yang bagus. Ini akan mencegah konflik penamaan, dan memungkinkan menggunakan nama variabel yang sama di fungsi yang berbeda.

### Passing Parameter

**Parameter** adalah informasi yang diperlukan oleh sebuah fungsi untuk bekerja. Parameter didefinisikan di antara tanda kurung `(...)` setelah nama fungsi. Parameter itu kemudian dapat digunakan didalam fungsi.

```js
function menyapa(nama) {
  console.log(`Halo ${nama}`);
}

console.log(menyapa("Satya")); // Halo Satya
console.log(menyapa("Angga")); // Halo Angga
```

Deklarasi fungsi `menyapa` kini terdapat parameter `nama`.

Dalam contoh ini pemanggilan pertama fungsi `menyapa` dilakukan dengan argument `Satya`, dan yang kedua `Angga`. Pada pemanggilan pertama parameternya adalah `Satya` sedangkan kedua `Angga`.

Berikut contoh syntax deklarasi fungsi dengan lebih dari 1 parameter, banyaknya parameter tidak dibatasi namun fungsi dengan parameter lebih dari 3 atau 4 jarang ditemukan.

```js
// Deklarasi fungsiSaya dengan beberapa parameter
function fungsiSaya(param1, param2, ...) {
  // Gunakan param1, param2, ... disini
}

// Pemanggilan fungsi
// nilai param1 diiisi dengan arg1, param2 diisi arg2, ...
fungsiSaya(arg1, arg2, ...);
```
