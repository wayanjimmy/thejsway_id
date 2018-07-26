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
    console.log('Halo');
}

console.log('Program dimulai');
menyapa();
console.log('Program selesai');
```

### Deklarasi fungsi

### Memanggil fungsi

### Manfaat menggunakan fungsi

Masalah yang kompleks umumnya lebih mudah ditangani ketika dipecah menjadi beberapa masalah yang lebih sederhana. Program komputer, ditulis sebagai kombinasi dari beberapa fungsi singkat dan terfokus, program akan lebih mudah dipahami dan diperbarui daripada yang monolitik. Sebagai bonus tambahan, beberapa fungsi dapat digunakan kembali di program lain!

Membuat fungsi juga bisa menjadi solusi untuk masalah duplikasi kode, Daripada kode diduplikasi di beberapa tempat, sepotong kode yang dijadikan fungsi dapat dipanggil dari mana saja ketika diperlukan.

### Passing Parameter

**Parameter** adalah informasi yang diperlukan oleh sebuah fungsi untuk bekerja. Parameter didefinisikan di antara tanda kurung `(...)` setelah nama fungsi. Parameter itu kemudian dapat digunakan didalam fungsi.

```js
function menyapa(nama) {
    console.log(`Halo ${nama}`);
}

console.log(menyapa('Satya')); // Halo Satya
console.log(menyapa('Angga')); // Halo Angga
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