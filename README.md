# htmltojsx

[![Build Status](http://img.shields.io/travis/tsuyoshiwada/htmltojsx.svg?style=flat-square)](https://travis-ci.org/tsuyoshiwada/htmltojsx)
[![npm (scoped)](https://img.shields.io/npm/v/@tsuyoshiwada/htmltojsx.svg?style=flat-square)](https://www.npmjs.com/package/@tsuyoshiwada/htmltojsx)

> HTML to JSX converter. Forked from [reactjs/react-magic](https://github.com/reactjs/react-magic). Support for SVG attributes.




## Table of Contents

* [What is different from the original?](#what-is-different-from-the-original)
* [Install](#install)
* [Usage](#usage)
* [Contribute](#contribute)
* [License](#license)




## What is different from the original?

The support of SVG is different from the original.  
You can convert attributes and tag names owned by SVG.

The conversion result differs as follows.

**Actual:**

```html
<svg class="foo">
  <defs>
    <linearGradient x1="75.9899742%" y1="91.918713%" x2="19.295843%" y2="7.23037329%" id="linearGradient-1">
      <stop stop-color="#FFF8B3" offset="0%"></stop>
      <stop stop-color="#E2CBE3" offset="100%"></stop>
    </linearGradient>
  </defs>
  <path fill-opacity="0.5" d="M144.296465,117.379726 L192.379726,69.2964646 L144.296465,21.2132034 L106.796465,58.7132034 L69.2964646,21.2132034 L21.2132034,69.2964646 L69.2964646,117.379726 L106.796465,79.8797257 L144.296465,117.379726 Z M69.2964646,138.592929 L0,69.2964646 L69.2964646,0 L106.796465,37.5 L144.296465,0 L213.592929,69.2964646 L144.296465,138.592929 L106.796465,101.092929 L69.2964646,138.592929 Z" id="Combined-Shape" fill="url(#linearGradient-1)"></path>
</svg>
```

**htmltojsx (original):**

```HTML
<svg className="foo">
  <defs>
    <lineargradient x1="75.9899742%" y1="91.918713%" x2="19.295843%" y2="7.23037329%" id="linearGradient-1">
      <stop stop-color="#FFF8B3" offset="0%" />
      <stop stop-color="#E2CBE3" offset="100%" />
    </lineargradient>
  </defs>
  <path fill-opacity="0.5" d="M144.296465,117.379726 L192.379726,69.2964646 L144.296465,21.2132034 L106.796465,58.7132034 L69.2964646,21.2132034 L21.2132034,69.2964646 L69.2964646,117.379726 L106.796465,79.8797257 L144.296465,117.379726 Z M69.2964646,138.592929 L0,69.2964646 L69.2964646,0 L106.796465,37.5 L144.296465,0 L213.592929,69.2964646 L144.296465,138.592929 L106.796465,101.092929 L69.2964646,138.592929 Z" id="Combined-Shape" fill="url(#linearGradient-1)" />
</svg>
```

* `<lineargradient>` is in lowercase letters. (Should be camel case)
* `fill-opacity` is in kebab-case letters. (Should be camel case)

**@tsuyoshiwada/htmltojsx (this package):**

```javascript
<svg className="foo">
  <defs>
    <linearGradient x1="75.9899742%" y1="91.918713%" x2="19.295843%" y2="7.23037329%" id="linearGradient-1">
      <stop stopColor="#FFF8B3" offset="0%" />
      <stop stopColor="#E2CBE3" offset="100%" />
    </linearGradient>
  </defs>
  <path fillOpacity="0.5" d="M144.296465,117.379726 L192.379726,69.2964646 L144.296465,21.2132034 L106.796465,58.7132034 L69.2964646,21.2132034 L21.2132034,69.2964646 L69.2964646,117.379726 L106.796465,79.8797257 L144.296465,117.379726 Z M69.2964646,138.592929 L0,69.2964646 L69.2964646,0 L106.796465,37.5 L144.296465,0 L213.592929,69.2964646 L144.296465,138.592929 L106.796465,101.092929 L69.2964646,138.592929 Z" id="Combined-Shape" fill="url(#linearGradient-1)" />
</svg>
```



## Install

```bash
$ npm install --save @tsuyoshiwada/htmltojsx
```




## Usage

```javascript
const HTMLtoJSX = require('@tsuyoshiwada/htmltojsx');

// Default options
const converter = new HTMLtoJSX({
  createClass: false, // default `true`
  indent: '  ',       // default `'  '`
});

const html = `
  <div class="foo bar" style="width: 400px; padding: 20px 5px; background: white;">
    <h2 data-value="foo">Support SVG attributes</h2>
    <svg height="100" width="100"><circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" fill-rule="evenodd"/></svg>
  </div>
`;

const result = converter.convert(html);

console.log(result);
/*
<div className="foo bar" style={{width: 400, padding: '20px 5px', background: 'white'}}>
  <h2 data-value="foo">Support SVG attributes</h2>
  <svg height={100} width={100}><circle cx={50} cy={50} r={40} stroke="black" strokeWidth={3} fill="red" fillRule="evenodd" /></svg>
</div>
*/
```




## Contribute

1. Fork it!
1. Create your feature branch: git checkout -b my-new-feature
1. Commit your changes: git commit -am 'Add some feature'
1. Push to the branch: git push origin my-new-feature
1. Submit a pull request :D

Bugs, feature requests and comments are more than welcome in the [issues](https://github.com/tsuyoshiwada/htmltojsx/issues).




## License

[MIT © tsuyoshiwada](./LICENSE)

