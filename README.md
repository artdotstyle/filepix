# FilePix
[![npm](https://img.shields.io/npm/v/filepix.svg?style=flat-square)](https://www.npmjs.com/package/filepix)

<center> <img src="./img/cover.png" /></center>


<p class="lead">powerful image converter package, it can convert images into a different
              formats, it includes below features:</br>
              convert pdf to word document</br>
              convert images to a single pdf file</br>
              convert pdf to multiple image file</br>
              convert png to jpg</br>
              convert base64 to jpg or png</br>
              compress image files </br>
              add watermarks or extra effects to your image files</br>
            </p>

<hr>

## Installation
Install via NPM:

```bash
npm install filepix
```
<p class="lead">Then you can <strong>require</strong> or <strong>import</strong> as usual:</p>

```javascript
const filepix = require("filepix");
```
```typescript
import * as filepix from "filepix";
```
<hr>

<h2>Convert images to PDF</h2>
this feature let you convert your images into a single pdf file
<h3>Basic Usage</h3>
<p class="lead mb-5">if you want to convert all images inside a specific directory you can use below code:
</p>
<p class="lead mb-10"><code>pages</code>: images directory path</br>
  <code>source</code>: output for saving final PDF file
</p>



```javascript
filepix.img2PDF(pages = './inputImagesDir', output = "./outputImageDir/output.pdf");
```
or maybe your images file in different path for this case you can use below code:

```javascript
filePix.img2PDF(
  pages = [
        './1.jpg',
        './public/upload/2.jpg',
        './public/upload/example/3.jpg'
  ],
  output = "./outputImageDir/output.pdf");
```

 <h3>Add Effects</h3>
<p class="lead mb-5">add easily a lot of effect to your images while converting to pdf
</p>
add effect to your final pdf by set some options.
#### Color
Apply multiple color modification rules

```javascript
let options = {
   effects: [
              {
                  name: 'color',
                  config: [{ apply: 'green', params: [100] }]
              }
            ]
  };
filepix.img2PDF(pages = './inputImagesDir', output = "./outputImageDir/output.pdf", options);
```

#### Flip
Flip the image horizontally or vertically. Defaults to horizontal.
```javascript
let options = {
   effects: [
              {
                  name: 'mirror'
              }
            ]
  };

```
```javascript
let options = {
   effects: [
              {
                name: 'flip',
                config: {
                    vertical: true
                }
              }
            ]
  };
filepix.img2PDF(pages = './inputImagesDir', output = "./outputImageDir/output.pdf", options);
```
#### Blur
A fast blur algorithm that produces similar effect to a Gaussian blur
```javascript
let options = {
   effects: [
              {
                name: 'blur',
                config: {
                    pixels: 50
                }
              }
            ]
  };
```
#### Rotate
Rotates the image clockwise by a number of degrees. By default the width and height of the image will be resized appropriately.
```javascript
let options = {
   effects: [
              {
                name: 'rotate',
                config: {
                    ratio: 45
                }
              }
            ]
};
```
#### Brightness
```javascript
let options = {
   effects: [
              {
                name: 'brightness',
                config: {
                    ratio: 0.1
                }
              }
            ]
};
```
#### Contrast
```javascript
let options = {
   effects: [
              {
                name: 'contrast',
                config: {
                    ratio: 0.2
                }
              }
            ]
  };
```
#### Gaussian

```javascript
let options = {
   effects: [
              {
                name: 'gaussian',
                config: {
                    ratio: 2
                }
              }
            ]
};
```

#### Posterize
```javascript
let options = {
   effects: [
              {
                name: 'posterize',
                config: {
                    ratio: 100
                }
              }
            ]
};
```
#### Opacity
```javascript
let options = {
   effects: [
              {
                name: 'opacity',
                config: {
                    ratio: 0.1
                }
              }
            ]
};
```
### Sepia
```javascript
let options = {
   effects: [
              {
                name: 'sepia'
              }
            ]
};
```

#### Quality
```javascript
let options = {
   effects: [
              {
                name: 'quality',
                config: {
                    ratio: 10
                }
              }
            ]
};
```
#### Fade
```javascript
let options = {
   effects: [
              {
                name: 'fade',
                config: {
                    ratio: 0.1
                }
              }
            ]
};
```
#### Pixelate
```javascript
let options = {
   effects: [
              {
                name: 'pixelate',
                config: {
                    ratio: 50
                }
              }
            ]
};
```
#### Normalize
```javascript
let options = {
   effects: [
              {
                name: 'normalize',
                config: {
                    ratio: 50
                }
              }
            ]
};
```
#### Threshold
```javascript
let options = {
   effects: [
              {
                name: 'threshold',
                config: { max: 200, replace: 200, autoGreyscale: false }
              }
            ]
};
```
#### multiple effects
you can combine effects by using below code:
```javascript
let options = {
   effects: [
            {
                name: 'quality',
                config: {
                    ratio: 10
                }
            },
            {
                name: 'contrast',
                config: {
                    ratio: 0.2
                }
            },
            {
              name: 'threshold',
              config: { max: 200 }
            }
          ]
};
```
### Add watermarks
you can add watermark to all images and merge them as single pdf by set below option
path: watermark image path
position: watermark position (center,right,right-bottom,center-bottom,left-top,left-bottom)

```javascript
options = {
  watermark: {
            type: 'image',
            path: '../logo1.jpg',
            ratio: 0.2,
            opacity: 0.2,
            position: 'left-bottom'
  }
}
```
<hr>

<h2>Convert pdf to images</h2>
this feature let you convert your pdf into multiple images.
<h3>Basic Usage</h3>

```javascript
filePix.PDF2img('./inputImagesDir/input.pdf', "./outputImageDir");
```
<hr>

<h2>Convert pdf to word document</h2>



> **_NOTE:_**  this method using OCR so first, you need to install the Tesseract project. Instructions for installing Tesseract for all platforms can be found on [the project site](https://github.com/tesseract-ocr/tessdoc/blob/master/Installation.md).

after installing Tesseract you can easily convert your pdf into file as docx format by calling below code:
```javascript
await filePix.pdf2docx('./inputImageDir/input.pdf', './outputImageDir/output.docx');
```
<hr>
<h2>Convert png to jpg</h2>
convert png format into jpg even you can compress your image.

```javascript
await filePix.png2jpeg('./input.png', './output.jpg'
, options = {
  quality: 50
});
```
<hr>
<h2>base64 to jpg or png</h2>
convert base64 to png or jpg by calling below method.

```javascript
await filePix.base64ToImg('base64Str', './outputImageDir/output.png', { extension: 'png' });
```
<hr>

## Support
  - [Bug Reports](https://github.com/hamedpa/filepix/issues/)

## Contributors
<p>
Pull requests are always welcome! Please base pull requests against the main branch and follow the contributing guide.

if your pull requests makes documentation changes, please update readme file.
</p>

## License

This project is licensed under the terms of the
MIT license