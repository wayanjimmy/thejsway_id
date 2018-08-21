# Mengenali Pemrograman Berorientasi Obyek

Beberapa bab sebelumnya Anda telah belajar bagaimana membuat object di Javascript. Sekarang saatnya mengenalinya dengan lebih baik.

## Rangkuman 

* **Pemrograman Berorientasi Objek** atau OOP adalah [paradigma pemrograman](https://en.wikipedia.org/wiki/Programming_paradigm) yang menggunakan Objek yang berisikan **data** dan **kelakuan** untuk membuat program.

* **Class** adalah sebuah abstraksi konsep atau ide dalam pemrograman berorientasi objek. Konsep ini menawarkan syntax yang nyaman dalam merepresentasikan objek.

* Dalam Javascript class didefinisikan dengan kata kunci `class`. Class hanya dapat berisikan **method**. Method `constructor()` yang dipanggil ketika object dibuat, digunakan untuk melakukan inisialisasi objek, biasanya digunakan untuk mengisikan properi pada objek. Didalam method, kata kunci `this` merepresentasikan **object dimana method itu dipanggil**.

```js
class SebuahClass {
  constructor(param1, param2, ...) {
    this.property1 = param1;
    this.property2 = param2;
  }
  method(/* ... */) {
    // ...
  }
  method2(/* ... */) {
    // ...
  }
  // ...
}
```

* Object dibuat dari class dengan menggunakan operator `new`. Ini akan memanggil construct dalam class atau inisialisasi object yang dibuat.

```js
const objekSaya = new SebuahClass(arg1, arg2, ...);
// ...
```

* Model OOP dalam Javacscript berdasarkan **prototype**. Setiap objek javascript memiliki internal property yang menghubungkan ke object lain yang disebut prototype. Prototype digunakan untuk berbagi propery dan menurunkan kelakuan antar objek.

* Ketika mencoba untuk mengakses property yang tidak ada dalam objek, Javascript mencoba untuk mencari property ini di dalam **rantai prototype** yang ada dalam objek, pertama mencari dalam prototypenya kemudian prototype dari prototype dan seterusnya.

* Ada beberapa cara untuk membuat dan menghubungkan object melalui prototype. Salah satunya menggunakan method `Object.create()`

```js
// Membuat object yang terhubungan dengan sebuahPrototype
const objekSaya = Object.create(sebuahPrototype);
```

* Syntax `class` pada javascript adalah cara yang nyaman untuk membuat hubungan antar objek. Dengan syntax ni OOP pada javacript menjadi mirip seperti OOP bahasa lain seperti C++, Java atau C#. Namun perlu diingat syntax ini hanya **syntactic sugar** yang dibuat diatas Javascript prototype.

## Konteks: Game RPG multiplayer

Sebagai pengingat, berikut adalah kode RPG minimal dari bab sebelumnya. Kode ini membuat objek literal yang bernama `aurora` dengan 4 properti (`name`, `health`, `strength`, `xp`) dan sebuah method `describe()`.

```js
const aurora = {
  name: "Aurora",
  health: 150,
  strength: 25,
  xp: 0,
    
  // Mengembalikan deskripsi karakter
  describe() {
    return `${this.name} memiliki ${this.health} health point, kekuatan ${this.strength} dan pengalaman ${this.xp}`;
  }
}

// Aurora terkena serangan panah
aurora.health -= 20;

// Aurora mendapat kekuatan dari kalung
aurora.strength += 10;

// Aurora belajar keahlian baru
aurora.xp += 15;

console.log(aurora.describe());
```

Untuk membuat permainan menjadi lebih menarik kita akan menambah sebuah karakter. Muncullah karakter Glacius, pengikut dari Aurora.

```js
const glacius = {
  name: "Glacius",
  health: 130,
  strength: 30,
  xp: 0,

  // Mengembalikan deskripsi karakter
  describe() {
    return `${this.name} memiliki ${this.health} health point, kekuatan ${this.strength} dan pengalaman ${this.xp}`;
  }
};
```

Kedua karakter tersebut memiliki kesamaan. Properti yang digunakan sama hanya nilainya saja yang berbeda.

Anda harus mengetahui bahwa duplikasi kode lebih baik untuk dihindari. Jadi kita harus mencari cara agar kedua objek tersebut bisa saling berbagi properti yang sama.

## Class di Javascript

Sebagian besar bahasa pemrograman yang mendukung orientasi objek menggunakan class sebagai **abstraksi** yang akan dimanipulasi oleh program. Class digunakan untuk membuat objek dan merepresentasikan konsep. Hal ini menawarkan syntax yang nyaman ketika memberikan **data** dan **kelakuan** pada objek tersebut.

Bukan pengecualian untuk Javascript yang mana javascript memberikan dukungan pemrograman menggunakan class (Namun dengan sedikit keanehan, akan dijelaskan nanti).

### Membuat Class

Contoh kode RPG diatas berurusan dengan karakter, jadi mari membuat sebuah class `Character` yang akan digunakan untuk menekspresikan apa itu sebuah karakter.

```js
class Character {
  constructor(name, health, strength) {
    this.name = name;
    this.health = health;
    this.strength = strength;
  }

  // Mengembalikan deskripsi karakter
  describe() {
    return `${this.name} memiliki ${this.health} health point, kekuatan ${this.strength} dan pengalaman ${this.xp}`;
  }
}
```

Contoh ini mendemonstrasikan beberapa fakta tentang class di javascript:

* Class dibuat dengan kata kunci `class` diikuti dengan nama class (biasanya diawali dengan huruf besar).
* Class hanya bisa berisikan **method**, bukan properti data.
* Seperti object literal, kata kunci `this` merujuk pada objek dimana method tersebut dipanggil
* Method khusus `constructor()` dapat ditambahkan ke definisi sebuah class. Akan dipanggil ketika objek tersebut dibuat dan biasanya digunakan untuk memberikan properti data.

### Menggunakan Class

Setelah class didefinisikan, Anda dapat membuat objek. Perhatikan program berikut ini.

```js
const auroroa = new Character("Aurora", 150, 25);
const glacious = new Character("Glacius", 130, 30);

// Aurora diserang dengan panah
aurora.health -= 20;

// Aurora mendapatkan kekuatan dari kalung
aurora.strength += 10;

// Aurora mempelajari keahlian baru
aurora.xp += 15;

console.log(aurora.describe()):
console.log(glacius.describe()):
```

![Execution result](images/chapter09-01.png)

Objek `aurora` dan `glacius` dibuat sebagai character dengan operator `new`. Pernyataan ini akan memanggil constructor dari class dan menginisialisasi sebuah objek. Setelah objek dibuat, objek memiliki akses untuk property yang ada didalamnya.

Berikut adalah syntax pembuatan objek dengan class.

```js
class MyClass {
  constructor(param1, param2, ...) {
    this.property1 = param1;
    this.property2 = param2;
    // ...
  }

  method(/* ... */) {
    // ...
  }

  method2(/* ... */) {
    // ...
  }

  // ...
}

const myObject = new MyClass(arg1, arg2, ...);
myObject.method1(/* ... */);
// ...
```
