[![Build Status](https://travis-ci.com/pevers/images-scraper.svg?branch=master)](https://travis-ci.com/pevers/images-scraper)

# images-scraper

This a simple way to scrape Google images using Puppeteer. The headless browser will behave as a 'normal' user and scrolls to the bottom of the page until there are enough results.

<p align="center">
    <img src="https://media.giphy.com/media/WSqsRhuPWPTrYtXAiN/giphy.gif">
</p>

# Installation

for the version with safesearch parameter:<br>
`npm install https://github.com/Mart100/images-scraper/tarball/master` 

Or for the original version:<br>
`npm install images-scraper`

# Example

Give me the first 200 images of Banana's from Google (using headless browser)

```js
var Scraper = require('images-scraper');

const google = new Scraper({
  puppeteer: {
    headless: false,
  }
});

(async () => {
  const results = await google.scrape('banana', 200);
  console.log('results', results);
})();
```

## Results
`node src/example.js`

```js
results [
  {
    url: 'https://api.time.com/wp-content/uploads/2019/11/gettyimages-459761948.jpg?quality=85&crop=0px%2C74px%2C1024px%2C536px&resize=1200%2C628&strip',
    source: 'https://time.com/5730790/banana-panama-disease/',
    description: 'Near-Extinction of Bananas ...'
  },
  ...
]
```


# Options

There are multiple options that can be passed to the constructor.

```js
var options = {
  userAgent: 'Mozilla/5.0 (X11; Linux i686; rv:64.0) Gecko/20100101 Firefox/64.0', // the user agent
  puppeteer: {}, // puppeteer options, for example, { headless: false }
  tbs: {  // every possible tbs search option, some examples and more info: http://jwebnet.net/advancedgooglesearch.html
    isz:  // options: l(arge), m(edium), i(cons), etc.
    itp:  // options: clipart, face, lineart, news, photo
    ic:   // options: color, gray, trans
    sur:  // options: fmc (commercial reuse with modification), fc (commercial reuse), fm (noncommercial reuse with modification), f (noncommercial reuse)
  }, 
};
```

# Debugging
Debugging can be done by disabling the headless browser and visually inspect the actions taken.

```js
const google = new Scraper({
  puppeteer: {
    headless: false,
  }
});
```

Or by settings the environment variable `LOG_LEVEL`.

`LOG_LEVEL=debug node src/example.js`.

# License

Copyright (c) 2019, Peter Evers <pevers90@gmail.com>

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.
THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
