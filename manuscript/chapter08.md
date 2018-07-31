# Bekerja dengan String

## Rangkuman

* Walaupun string adalah tipe primitif di Javascript, tapi ada beberapa **properti** dan **method** yang bisa diterapkan.

* Properti `length` mengembalikan banyak karakter dalam string tersebut.

* String di Javascript bersifat  **[immutable]( https://en.wikipedia.org/wiki/Immutable_object )**: ketika dibuat, nilai string tidak akan berubah. Method dalam object string tidak akan pernah mengubah nilai awalnya namun akan selalu mengembalikan nilai baru.

* Method `toLowerCase()` dan `toUpperCase()` mengembalikan nilai baru string berupa huruf kecil dan huruf besar.

* String dapat dilihat sebagai array yang terdiri dari karakter. Dengan indeks pertama adalah 0.

* Anda bisa melakukan iterasi terhadap string dengan `for` atau `for-of`.

* Menggunakan method `Array.from()` Anda bisa mengubah string menjadi array yang terdiri atas karakter baru setelahnya anda dapat menggunakan `forEach()` untuk mengiterasikannya.

* Melakukan pencarian didalam string dapat menggunakan method `indexOf()`, `startsWith()` dan `endsWith()`.

* Method `split()` dapat digunakan untuk memecah string berdasarkan sebuah karakter pemisah. 

## Pengenalan String 

Mari ulas lagi apa yang telah dipelajari tentang String:

* Nilai string merepresentasikan teks.

* Di javascript, string didefinisikan dalam teks yang diapit oleh kutip satu (`'Saya string'`) atau kutip dua (`"Saya string"`).

* Karakter khusus dalam string diawali dengan (`\`) diikuti dengan karakter khusus tersebut. Contoh `\n` adalah karakter khusus untuk menambahkan baris baru.

* Operator tambah `+` digunakan untuk menggabungkan dua atau lebih string.

## Mendapatkan panjang string

Untuk mendapatkan panjang sebuah string, tinggal menambahkan `.length`. Panjang string akan dikembalikan dalam bentuk bilangan bulat.

```js
console.log("ABC".length); // 3
const str = "Saya string";
const len = str.length;
console.log(len); // 11
```

Walaupun string termasuk dalam tipedata primitif, beberapa properti dan method dapat diaplikasikan seperti halnya object, salah satunya adalah properti `.length`.

## Mengubah case string

Untuk mengubah string menjadi huruf kecil dapat digunakan method `toLowerCase()`, sedangkan `toUpperCase()` digunakan untuk mengubah jadi huruf besar.

