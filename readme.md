![PrintHub](https://defuj.github.io/printhub/assets/images/printhub.webp)

# PrintHub

[![npm version](https://badge.fury.io/js/printhub.svg)](https://badge.fury.io/js/printhub)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

PrintHub is a JavaScript plugin for printing text using a Bluetooth or USB thermal printer. Demo: [PrintHub Demo](https://defuj.github.io/printhub/)

## Features

1. Print text with various options like bold, underline, alignment, and text size.
2. Print text in two columns.
3. Print dashed lines.
4. Print line breaks.
5. Supports two paper sizes: "58mm" and "80mm".
6. Supports connecting to Bluetooth thermal printers.
7. Compatible with modern browsers such as Chrome, Firefox, and Edge.
8. Node.js compatible.
9. Supports usage via CDN.
10. Supports usage via NPM.
11. ES6 compatible.

## Installation

### Using NPM

```bash
npm install printhub
```

Import or require PrintHub into your project.

```javascript
import PrintHub from "printhub";
```

or

```javascript
const PrintHub = require("printhub");
```

### Using CDN

```html
<script src="https://cdn.jsdelivr.net/npm/printhub@1.0.13/dist/index.global.js"></script>
```

## Usage

### Creating a PrintHub Instance

You can create an instance of PrintHub with or without specifying the desired paper size. Supported paper sizes are "58" and "80". If the paper size is not specified, the default is "58".

1. Creating a PrintHub instance with "80" paper size

   ```javascript
   let printer = new PrintHub.init({
     paperSize: "80",
   });
   ```

2. Creating a PrintHub instance with "58" paper size

   ```javascript
   let printer = new PrintHub.init();
   ```

### Selecting Printer Type

You can select the type of printer to use. Supported types are "bluetooth" and "usb". If the printer type is not specified, the default is "bluetooth".

1. Selecting "bluetooth" printer type

   ```javascript
   let printer = new PrintHub.init({
     printerType: "bluetooth",
   });
   ```

2. Selecting "usb" printer type

   ```javascript
   let printer = new PrintHub.init({
     printerType: "usb",
   });
   ```

### Connecting to Printer and Printing Text

Use the `connectToPrint` method to connect to a Bluetooth printer and print text. You need to provide two callback functions: `onReady` and `onFailed`.

| Callback   | Description                                                                                                           |
| ---------- | --------------------------------------------------------------------------------------------------------------------- |
| `onReady`  | Called when the printer connection is successful. You can use the print object passed to this callback to print text. |
| `onFailed` | Called when the printer connection fails. You can use the message parameter to get the error message.                 |

### How to Use PrintHub

1. Connect to the printer and print text.

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

2. Print bold text.

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

3. Print underlined text.

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

4. Print text with alignment.

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

5. Print text with a specific size.

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

6. Print text in two columns.

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

7. Print dashed lines.

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

8. Print line breaks.

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

9. Print text with multiple options.

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

10. Print text with multiple options in two columns.

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

| Method                                        | Description                                                             |
| --------------------------------------------- | ----------------------------------------------------------------------- |
| `writeLineBreak({ count = 1 })`               | Writes a line break.                                                    |
| `writeDashLine()`                             | Writes a dashed line.                                                   |
| `writeTextWith2Column(text1, text2, options)` | Writes text in two columns.                                             |
| `writeText(text, options)`                    | Writes text.                                                            |
| `connectToPrint({ onReady, onFailed })`       | Connects to the printer and calls the `onReady` or `onFailed` callback. |

### Options for `writeText` and `writeTextWith2Column` Methods

| Option      | Description                                                            | Default  |
| ----------- | ---------------------------------------------------------------------- | -------- |
| `bold`      | Specifies whether the text is printed in bold.                         | `false`  |
| `underline` | Specifies whether the text is printed with an underline.               | `false`  |
| `align`     | Specifies text alignment. Supported values: "left", "center", "right". | `left`   |
| `size`      | Specifies the text size. Supported values: "normal", "double".         | `normal` |

## Requirements for USB Printer

### Windows

1. Install [Zadig](https://zadig.akeo.ie/).
2. Connect the USB Printer to your computer.
3. Open Zadig and select your USB Printer.
4. Install the WinUSB driver for your USB Printer.
5. Done.

### Linux

1. Connect the USB Printer to your computer.
2. Open the terminal and run `lsusb`.
3. Find your USB Printer and note the vendor id and product id.
4. Run `sudo modprobe usblp`.
5. Run `sudo echo "ATTRS{idVendor}=="YOUR_VENDOR_ID", ATTRS{idProduct}=="YOUR_PRODUCT_ID", MODE="0666", GROUP="plugdev" > /etc/udev/rules.d/99-usb-printer.rules`.
6. Run `sudo udevadm control --reload-rules`.
7. Run `sudo udevadm trigger`.
8. Done.

### macOS

1. Connect the USB Printer to your computer.
2. Open the terminal and run `ls /dev/cu.*`.
3. Find your USB Printer and note the device name.
4. Run `sudo chmod
5. Run `sudo chown
6. Done.

## Browser Support

### Desktop

| Browser | Version | Status |
| ------- | ------- | ------ |
| Chrome  | 61      | ✔️     |
| Firefox | No      | ❌     |
| Edge    | 79      | ✔️     |
| Safari  | No      | ❌     |
| Opera   | 48      | ✔️     |

### Mobile

| Browser | Version | Status |
| ------- | ------- | ------ |
| Chrome  | 61      | ✔️     |
| Firefox | No      | ❌     |
| Safari  | No      | ❌     |
| Opera   | 45      | ✔️     |
| Samsung | 8.0     | ✔️     |
| WebView | No      | ❌     |

## Change Log

### v1.0.13

- Add support for Node.js (typescript, es6, commonjs)
- Change the way to use instance of PrintHub

### v1.0.7

- Fix writeTextWith2Column method if length of text1 + text2 is greater than 32 or 42 characters

### v1.0.6

- Remove unused code

### v1.0.5

- Update paper size from "58mm" and "80mm" to "58" and "80"

### v1.0.4

- Added instructions for USB Printer on Windows, Linux, and macOS

### v1.0.3

- Fixed USB Printer not working
