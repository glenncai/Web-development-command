# Web Development Useful Command

> devDependencies (Development Environment), when we install the package, we should add `--save-dev`

> Dependencies (Production Environment), when we install the package, we should add `--save`

<br>

### Install node_modules folder

***command:*** `npm install`

---

<br>

### Create package.json file

***command:*** `npm init`

---

<br>

### Install live-server:

***command:*** `sudo npm install live-server -g` (install in user computer)

***usage:*** move to the target folder, and run `live-server`

---

<br>

### Install node-sass

***command:*** `npm install node-sass --save-dev`

---

<br>

### Concatenate multiple files

***command:*** `npm install concat --save-dev`

***use in package.json:*** `concat -o css/style.concat.css css/icon-font.css css/style.comp.css`
* `-o` means output, 
* `style.concat.css` is the output file of concatenating multiple files 
* `css/icon-font.css css/style.comp.css` are the files what we wanna concatenate

---

<br>

### Install Autoprefixer

> Add vendor prefixes to CSS rules using values from [Can I Use](https://caniuse.com/).

***command:*** `npm install concat --save-dev`

---

<br>

### Install Postcss-cli

> Autoprefixer is the part of Postcss-cli plugin

***command:*** ` npm install postcss-cli --save-dev`

***use in package.json:*** `"prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css"`
* NOTE: ensure you have install `Autoprefixer` and `Postcss-cli`
* `-b` means browsers
* `last 10 version` means the lastest ten browsers version support
* `css/style.concat.css` is input file
* `css/style.prefix.css"` is output file

---

<br>

### Install npm-run-all

> A CLI tool to run multiple npm-scripts in parallel or sequential.

***command:*** `npm install npm-run-all --save-dev`

---

<br>

## Scripts that I created:

```json
{
  "name": "sample",
  "version": "1.0.0",
  "description": "sample",
  "main": "index.js",
  "scripts": {
    "watch:sass": "node-sass sass/main.scss css/style.css -w",
    "devserver": "live-server",
    "start": "npm-run-all --parallel devserver watch:sass",
    
    "compile:sass": "node-sass sass/main.scss css/style.comp.css",
    "concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
    "prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css",
    "compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
    "build:css": "npm-run-all compile:sass concat:css prefix:css compress:css"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "autoprefixer": "^10.2.4",
    "concat": "^1.0.3",
    "node-sass": "^5.0.0",
    "npm-run-all": "^4.1.5",
    "postcss-cli": "^8.3.1"
  }
}
```
> For Development, run `npm run start`

> For Production, run `npm run build:css`