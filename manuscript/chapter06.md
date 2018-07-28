# Membuat object pertama anda

Pada bab ini akan dikenalkan object dan cara mereka dibuat dan digunakan dalam JavaScript.

## TL;DR

* Object di JavaScript adalah entitas yang memiliki property. Setiap property adalah sepasang key/value. Key adalah nama property.

* Nilai dari property dapat berupa bagian informasi (number, string, dan lain-lain) atau fungsi. 
Dalam kasus tertentu, property bisa dianggap sebagai **method**.

* JavaScript **object literal** dibuat menggunakan tanda kurung kurawal `{}`.

```js
const myObject = {
  property1: value1,
  property2: value2,
  // ... ,
  method1(/* ... */) {
    // ...
  },
  method2(/* ... */) {
    // ...
  }
  // ...
};

myObject.property1 = newValue; // Memasang nilai baru pada property1 pada myObject
console.log(myObject.property1); // Menampilkan nilai pada property1 pada myObject
myObject.method1(...);           // Memanggil method1 pada myObject
```

* Di dalam sebuah method, kata kunci `this` mewakili object terhadap method yang dipanggil.

* JavaScript telah menyediakan beberapa object yang berguna seperti `console` or `Math`.

## Pengenalan

### Apa itu object?

Mari kita bayangkan object dalam dunia non programming, contohnya pulpen. Sebuah pulpen memiliki warna tinta yang berbeda, diproduksi oleh orang yang berbeda, memiliki ujung pena yang berbeda, dan banyak property lainnya.

Demikian pula, sebuah **object** dalam programming adalah **entitas yang memiliki banyak property**. Setiap property mendefinisikan karakteristik object. Sebuah property dapat berupa potongan informasi yang diasosiasikan dengan object 
(warna pulpen) atau sebuah aksi (kemampuan pulpen untuk menulis).

### Apa hubungannya dengan menulis kode?

**pemrograman berbasis objek** (PBO) adalah cara menulis program menggunakan object. Ketika menggunakan PBO, Anda menulis, membuat dan modifikasi object, dan object menyusun program Anda.

PBO mengubah cara sebuah program ditulis dan diorganisir. Sejauh ini, Anda telah menulis code berbasis fungsi, kadang disebut dengan [procedural programming](https://en.wikipedia.org/wiki/Procedural_programming). Sekarang mari kita coba cara menulis kode berbasis object.

## JavaScript dan objects

Seperti bahasa lainnya, JavaScript mendukung programming dengan object. JavaScript menyediakan sejumlah objek yang telah ditentukan sementara juga memungkinkan Anda membuat sendiri.

### Membuat sebuah object object

Ini adalah JavaScript gambaran pulpen merk Bic dengan warna biru.

```js
const pen = {
  type: "ballpoint",
  color: "blue",
  brand: "Bic"
};
```

Seperti yang dijelaskan sebelumnya, sebuah object di JavaScript dapat dibuat property nya dengan menggunakan kurung kurawal `{...}`.
Setiap property berisi sepasang key/value. Ini disebut dengan **object literal**.

> Tanda titik koma setelah tutup kurung kurawal bersifat opsional, tapi tidak masalah jika tidak ditambahkan.

Kode diatas di definisikan dalam sebuah variable bernama `pen` yang mana nilainya adalah object: Anda bisa mengatakan `pen` adalah object.
Object ini memiliki tiga property: `type`, `color` dan `brand`. Setiap property memiliki sebuah nama dan sebuah nilai yang diikuti dengan tanda koma setelahnya (kecuali yang terakhir).

### Mengakses sebuah property object

Setelah membuat sebuah object, Anda dapat mengakses nilai dari properti tersebut dengan menggunakan **dot notation** seperti `myObject.myProperty`.

```js
const pen = {
  type: "ballpoint",
  color: "blue",
  brand: "Bic"
};

console.log(pen.type);  // "ballpoint"
console.log(pen.color); // "blue"
console.log(pen.brand); // "Bic"
```

Mengakses sebuah object property adalah sebuah **expression** untuk menghasilkan nilai. Ekspresi semacam itu dapat dimasukkan ke dalam yang lebih kompleks.
Sebagai contoh, berikut adalah cara untuk menampilkan property pen dalam satu baris.

```js
const pen = {
  type: "ballpoint",
  color: "blue",
  brand: "Bic"
};

console.log(`I write with a ${pen.color} ${pen.brand} ${pen.type} pen`);
```

![Hasil eksekusi](images/chapter06-01.png)

### Memodifikasi sebuah object

Ketika object dibuat, Anda dapat mengubah nilai dari property tersebut dengan sintaks `myObject.myProperty = newValue`.

```js
const pen = {
  type: "ballpoint",
  color: "blue",
  brand: "Bic"
};

pen.color = "red"; // Memodifikasi property warna pulpen

console.log(`I write with a ${pen.color} ${pen.brand} ${pen.type} pen`);
```

![Hasil eksekusi](images/chapter06-02.png)

Bahkan JavaScript menawarkan kemampuan untuk menambahkan sebuah property baru terhadap object yang sudah dibuat secara dinamis.

```js
const pen = {
  type: "ballpoint",
  color: "blue",
  brand: "Bic"
};

pen.price = "2.5"; // Memasang properti harga pulpen

console.log(`My pen costs ${pen.price}`);
```

![Hasil eksekusi](images/chapter06-03.png)

## Programming dengan object

Banyak puku dan kursus mengajarkan pemrograman berbasis objek melalui banyak contoh seperti hewan, mobil atau rekening bank. Mari kita coba sesuatu yang keren dan membuat mini-role playing game (RPG) menggunakan object.

Dalam role-playing game, setiap karakter didefinisikan dengan banyak atribut seperti kekuatan, stamina, atau kecerdasan. Berikut adalah karakter layar RPG online yang sangat populer.

![Bukan, bukan milik saya!](images/chapter06-04.png)

Dalam contoh sederhana kami, karakter akan memiliki tiga atribut:

* name,
* health (angka poin nyawa),
* strength.

### Sebuah contoh sederhana

Mari saya kenalkan Aurora kepada Anda, karakter pertama RPG kita.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25
};
```

Object `aurora` memiliki tiga property: `name`, `health` and `strength`.

> Seperti yang Anda lihat, Anda dapat memberikan number, string bahkan object lainnya ke dalam properties!

Aurora akan memulai seri petualangan besar, kita harus mengubah atributnya. Lihat contoh di bawah.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25
};

console.log(`${aurora.name} has ${aurora.health} health points and ${aurora.strength} as strength`);

// Aurora diserang dengan panah
aurora.health -= 20;

// Aurora memasang kalung keuatan
aurora.strength += 10;

console.log(`${aurora.name} has ${aurora.health} health points and ${aurora.strength} as strength`);
```

![Hasil eksekusi](images/chapter06-05.png)

### Pengenalan method

Pada kode di atas, kita menulis sebuah pernyataan yang panjang dengan `console.log` setiap kali menampilkan keadaan karakter. Terdapat cara cerdas untuk menyelesaikan ini.

#### Menambahkan method ke dalam object

Amati contoh di bawah.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25
};

// Mengembalikan deskripsi karakter
function describe(character) {
  return `${character.name} has ${character.health} health points and ${character.strength} as strength`;
}

console.log(describe(aurora));
```

![Hasil eksekusi](images/chapter06-07.png)

The `describe()` function takes an object as a parameter. It accesses that object's properties to create a description string.

Below is an alternative approach, using a `describe()` property *inside* the object.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25,

  // Mengembalikan deskripsi karakter
  describe() {
    return `${this.name} has ${this.health} health points and ${this
      .strength} as strength`;
  }
};

console.log(aurora.describe());
```

![Hasil eksekusi](images/chapter06-07.png)

Sekarang object kita memiliki property baru bernama `describe()`. Nilai dari property ini adalah sebuah fungsi untuk mengembalikan deskripsi dari object tadi. Hasil eksekusi sama persis dengan sebelumnya.

Sebuah property object yang memiliki value berupa fungsi disebut dengan **method**. Method digunakan untuk mendefinisikan **actions** pada sebuah object. Sebuah method memiliki beberapa **behavior** pada sebuah object.

#### Memanggil method pada sebuah object

Mari kita lihat baris terakhir pada contoh sebelumnya.

```js
console.log(aurora.describe());
```

Untuk menampilkan deskripsi karakter, kita gunakan ekspresi `aurora.describe()` daripada `describe(aurora)`. Hal ini membuat perbedaan yang *besar*:

* `describe(aurora)` memanggil fungsi `describe()` dengan object `aurora` sebagai argument. Fungsi tersebut di luar dari object. Ini adalah contoh dari programming prosedural.

* `aurora.describe()` memanggil fungsi `describe()` pada object `aurora`. Fungsi tersebut adalah salah satu dari object properties: sebuah method. Ini adalah contoh dari pemrograman berbasis objek.

Untuk memanggil sebuah method bernama `myMethod()` pada object `myObject`, sintaksnya adalah `myObject.myMethod()`.

> Ingatlah tanda kurung `()` bahkan jika kosong ketika memanggil method!

### Kata kunci `this`

Sekarang lihat lebih dekat isi method `describe()` pada object kita.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25,

  // Mengembalikan deskripsi karakter
  describe() {
    return `${this.name} has ${this.health} health points and ${this
      .strength} as strength`;
  }
};
```

Anda melihat keyword baru: `this`. `This` secara otomatis dipasang oleh JavaScript di dalam sebuah method dan mewakili **object yang mana method nya dipanggil**.

Method `describe()` tidak mengambil parameter apapun. Ia menggunakan `this` untuk mengakses property sebuah object yang dipanggil.

## Object standar JavaScript

Bahasa JavaScript memiliki banyak object standar yang digunakan untuk kepentingan yang beragam. Kita sudah menggunakan beberapa diantaranya:

* Object `console` memberikan akses pada lingkungan console. `console.log()` sebenarnya adalah method pemanggil.

* Object `Math` berisi banyak property matematis. Contoh, `Math.PI` mengembalikan perkiraan nilai pada angka π (Pi) dan fungsi `Math.random()` mengembalikan nilai acak antara 0 dan 1.

## Waktunya Koding!

### Menambahkan pengalaman karakter

Improvisasi contoh program RPG untuk menambahkan sebuah property pengalaman dengan nama `xp` pada karakter. Ia diinisialisasi dengan nilai 0. Pengalaman harus muncul pada deskripsi karakter.

```js
// TODO: Buat object character di sini

// Aurora is harmed by an arrow
aurora.health -= 20;

// Aurora diserang dengan panah
aurora.strength += 10;

// Aurora belajar kemampuan baru
aurora.xp += 15;

console.log(aurora.describe());
```

![Hasil eksekusi](images/chapter06-08.png)

### Memodelkan seekor anjing

Lengkapi program di bawah untuk menambahkan object seekor `anjing`.

```js
// TODO: Membuat object anjing di sini

console.log(`${anjing.name} adalah spesies ${anjing.species} anjing dengan ukuran ${anjing.size}`);
console.log(`Lihat, seekor kucing! ${anjing.name} mengonggong: ${anjing.bark()}`);
```

![Hasil eksekusi](images/chapter06-09.png)

### Memodelkan sebuah lingkaran

Lengkapi program di bawah untuk menambahkan object sebuah `lingkaran`. Nilai jari-jari diinputkan oleh pengguna.

```js
const r = Number(prompt("Masukkan jari-jari lingkaran:"));

// TODO: Membuat object lingkaran di sini

console.log(`Jari-jarinya adalah ${circle.circumference()}`);
console.log(`Luasnya adalah ${circle.area()}`);
```

### Memodelkan sebuah akun bank

Tulislah sebuah program yang membuat sebuah object `account` dengan karakteristik berikut:

* Property `name` dipasang "Alex".
* Property `balance` dipasang 0.
* Method `credit` menambahkan nilai (positif atau negatif) sebagai argument pada account balance.
* Method `describe` mengembalikan deskripsi account.

Gunakan object ini untuk menampilkan deskripsi, kredit 250, debit 80, kemudian tampilkan lagi.

![Hasil eksekusi](images/chapter06-10.png)