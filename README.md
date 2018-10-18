# Intro
- This is a JavaScript library to make MSIE behave like a standards-compliant browser.
- It fixes many CSS issues and makes transparent PNG work correctly under IE5 and IE6.
- Check out this [demo page](https://seancoyne.github.io/ie7-js/) for more details.

# Getting started
- Get the library via npm: `npm install -S ie7js`
- There are 3 scripts: `IE7.js`, `IE8.js` and `IE9.js`.   They are backward compatible, which means the functionality that `IE7.js` and `IE8.js` has are included in `IE9.js` .     
- Basically what you need to do is:
  ```html
  <!--[if lt IE 9]>
  <script type="text/javascript" src="IE9.min.js"></script>
  <![endif]-->
  ```
- **IMPORTANT**: These CSS hacks take NO effect on inline styles, but support both internal and external stylesheets.

## PNG
- The script only fixes images named: `*-trans.png`
- If you want the fix to apply to all PNG images then set a global variable as follows:
  ```javascript
  var IE7_PNG_SUFFIX = ".png";
  ```
- You must set this variable before including the IE7.js script. Alternatively, you can set the variable inside the IE7.js script element:
  ```html
  <script src="IE9.min.js">IE7_PNG_SUFFIX=".png";</script>
  ```
- The suffix will ignore query string parameters. For more fine-grained control you can also set `IE7_PNG_SUFFIX` to a RegExp object. If you want to use an alternative PNG solution then set the suffix to something that cannot possibly match:
  ```javascript
  var IE7_PNG_SUFFIX = ":";
  ```
- By default, the PNG will be stretched (this simulates tiling). If you want to turn this off then set the no-repeat property as follows:
  ```css
  div.example {
    background: url("my-trans.png") no-repeat;
  }
  ```
- Unfortunately, the transparent background image cannot be tiled (repeated) using `background-repeat`. Nor can it be positioned using `background-position`.

# Credits and Links
![GitHub license](https://img.shields.io/github/license/ben-yip/ie7js.svg)
- This library is credited by [Dean Edwards](http://dean.edwards.name/), the copy in this repo is of its last and latest version 2.1(beta4).
- I put it here in GitHub for the convenience of management by NPM and integration in your own build workflow.
- Original repo hosted on Google: https://code.google.com/archive/p/ie7-js/
- Google groups:  https://groups.google.com/forum/#!forum/ie7-js
- Related posts:
  - http://dean.edwards.name/weblog/2008/01/ie7-2/
  - http://dean.edwards.name/weblog/2010/03/ie7js-update/
