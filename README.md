# serve-marked

[![repo][github-src]][github-link]
[![version][npm-badge]][npm-link]
[![size][size-badge]][size-link]
![ISC][license-src]

Serve [marked][marked] rendered README.md file.

## Usage

`npm i serve-marked`

```javascript
const http = require('http')
const serveMarked = require('serve-marked')

const serveReadme = serveMarked('./README.md')

http.createServer((req, res) => {
  if (req.url === '/') return serveReadme(req, res)
}).listen(3000)
```

or you can use options:

```javascript
// All options are optional
const serveReadme = serveMarked('./README.md', {
  title: 'Awesome Project',
  preset: 'merri',  // Available presets: 'default', 'merri'
  contentClassName: 'main-body', // Default: 'markdown-body'
  inlineCSS: `
    @import url('https://rsms.me/inter/inter-ui.css');
    body { color: #333 }
  `,
  beforeHeadEnd: '<meta name="description" content="...">',
  beforeBodyEnd: '<script>/*...*/</script>',
  trackingGA: 'UA-XXXXXX-X'
})
```

## Example

- https://serve-marked.now.sh ([src][now-index-src])

[github-src]: https://badgen.net/badge//amio%2Fserve-marked/black?icon=github
[github-link]: https://github.com/amio/serve-marked
[license-src]: https://badgen.net/badge/license/ISC/blue
[npm-badge]: https://badgen.net/npm/v/serve-marked
[npm-link]: https://www.npmjs.com/package/serve-marked
[size-badge]: https://badgen.net/bundlephobia/min/serve-marked
[size-link]: https://bundlephobia.com/result?p=serve-marked
[marked]: https://github.com/markedjs/marked
[now-index-src]: https://github.com/amio/serve-marked/blob/master/now-index.js
