# htmltojsx

[![Build Status](http://img.shields.io/travis/tsuyoshiwada/htmltojsx.svg?style=flat-square)](https://travis-ci.org/tsuyoshiwada/htmltojsx)

> HTML to JSX converter. Forked from [reactjs/react-magic](https://github.com/reactjs/react-magic). Support for SVG attributes.




## Table of Contents

* [What is different from the original?](#what-is-different-from-the-original)
* [Install](#install)
* [Usage](#usage)
* [Contribute](#contribute)
* [License](#license)




## What is different from the original?

It differs only in that SVG attributes can be converted! Other than that it is the same as the original.

I am sending a [patch PR](https://github.com/reactjs/react-magic/pull/136) to the original.  
If PR is merged, this package is unnecessary.




## Install

```bash
$ npm install --save @tsuyoshiwada/htmltojsx
```




## Usage

```javascript
const HTMLtoJSX = require('@tsuyoshiwada/htmltojsx');

// Default options
const converter = new HTMLtoJSX({
  createClass: true,
  indent: '  ',
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

