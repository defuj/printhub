# PrintHub

[![npm version](https://badge.fury.io/js/printhub.svg)](https://badge.fury.io/js/printhub)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

PrintHub adalah plugin JavaScript untuk mencetak teks menggunakan printer thermal Bluetooth atau USB Printer. Plugin ini mendukung dua ukuran kertas: "58mm" dan "80mm".

## Fitur

1. Mencetak teks dengan berbagai opsi seperti huruf tebal, garis bawah, perataan, dan ukuran teks.
2. Mencetak teks dengan dua kolom.
3. Mencetak garis putus-putus.
4. Mencetak baris baru.
5. Mendukung dua ukuran kertas: "58mm" dan "80mm".
6. Mendukung koneksi ke printer thermal Bluetooth.
7. Mendukung browser modern seperti Chrome, Firefox, dan Edge.
8. Mendukung Node.js.
9. Mendukung penggunaan CDN.
10. Mendukung penggunaan NPM.
11. Mendukung penggunaan ES6.

## Instalasi

### Menggunakan NPM

```bash
npm install printhub
```

import atau require PrintHub ke dalam proyek Anda.

```javascript
import PrintHub from "printhub";
```

or

```javascript
const PrintHub = require("printhub");
```

### Menggunakan CDN

```html
<script src="https://cdn.jsdelivr.net/npm/printhub@1.0/index.min.js"></script>
```

## Penggunaan

### Membuat Instance dari PrintHub

Anda dapat membuat instance dari PrintHub dengan atau tanpa menentukan ukuran kertas yang diinginkan. Ukuran kertas yang didukung adalah "58mm" dan "80mm". Jika ukuran kertas tidak ditentukan, ukuran kertas default adalah "58mm".

1. Membuat Instance PrintHub dengan Ukuran Kertas "80mm"

```javascript
let printer = new PrintHub({
  paperSize: "80mm",
});
```

2. Membuat Instance PrintHub dengan Ukuran Kertas "58mm"

```javascript
let printer = new PrintHub();
```

### Memilih Jenis Printer

Anda dapat memilih jenis printer yang akan digunakan. Jenis printer yang didukung adalah "bluetooth" dan "usb". Jika jenis printer tidak ditentukan, jenis printer default adalah "bluetooth".

1. Memilih Jenis Printer "bluetooth"

```javascript
let printer = new PrintHub({
  printerType: "bluetooth",
});
```

2. Memilih Jenis Printer "usb"

```javascript
let printer = new PrintHub({
  printerType: "usb",
});
```

### Menghubungkan ke Printer dan Mencetak Teks

Gunakan metode `connectToPrint` untuk menghubungkan ke printer Bluetooth dan mencetak teks. Anda perlu menyediakan dua fungsi callback: `onReady` dan `onFailed`.

| Callback   | Deskripsi                                                                                                                             |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `onReady`  | Dipanggil ketika koneksi ke printer berhasil. Anda dapat menggunakan objek print yang diteruskan ke callback ini untuk mencetak teks. |
| `onFailed` | Dipanggil ketika koneksi ke printer gagal. Anda dapat menggunakan parameter message untuk mendapatkan pesan error.                    |

### Cara Menggunakan PrintHub

1. Hubungkan ke printer dan cetak teks.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!");
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

2. Cetak teks dengan huruf tebal.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!", { bold: true });
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

3. Cetak teks dengan garis bawah.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!", { underline: true });
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

4. Cetak teks dengan perataan.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!", { align: "center" });
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

5. Cetak teks dengan ukuran teks.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!", { size: "double" });
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

6. Cetak teks dengan dua kolom.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeTextWith2Column("Name", "John Doe");
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

7. Cetak garis putus-putus.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeDashLine();
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

8. Cetak baris baru.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeLineBreak();
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

9. Cetak teks dengan berbagai opsi.

   ```javascript
   printer.connectToPrint({
     onReady: async (print) => {
       await print.writeText("Hello, World!", {
         bold: true,
         underline: true,
         align: "center",
         size: "double",
       });
     },
     onFailed: (message) => {
       console.log(message);
     },
   });
   ```

10. Cetak teks dengan berbagai opsi dan dua kolom.

    ```javascript
    printer.connectToPrint({
      onReady: async (print) => {
        await print.writeTextWith2Column("Name", "John Doe", {
          bold: true,
          underline: true,
          align: "center",
          size: "double",
        });
      },
      onFailed: (message) => {
        console.log(message);
      },
    });
    ```

### API

| Metode                                        | Deskripsi                                                                  |
| --------------------------------------------- | -------------------------------------------------------------------------- |
| `writeLineBreak({ count = 1 })`               | Menulis baris baru.                                                        |
| `writeDashLine()`                             | Menulis garis putus-putus.                                                 |
| `writeTextWith2Column(text1, text2, options)` | Menulis teks dengan dua kolom.                                             |
| `writeText(text, options)`                    | Menulis teks.                                                              |
| `connectToPrint({ onReady, onFailed })`       | Menghubungkan ke printer dan memanggil callback `onReady` atau `onFailed`. |

### Opsi untuk Metode `writeText` dan `writeTextWith2Column`

| Opsi        | Deskripsi                                                                 | Default    |
| ----------- | ------------------------------------------------------------------------- | ---------- |
| `bold`      | Menentukan apakah teks dicetak dengan huruf tebal.                        | `false`    |
| `underline` | Menentukan apakah teks dicetak dengan garis bawah.                        | `false`    |
| `align`     | Menentukan perataan teks. Nilai yang didukung: "left", "center", "right". | `"left"`   |
| `size`      | Menentukan ukuran teks. Nilai yang didukung: "normal", "double".          | `"normal"` |
