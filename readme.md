# remark-yaml-config

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Chat][chat-badge]][chat]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]

Configure [**remark**][remark] with YAML front-matter.  This requires
[`remark-frontmatter`][remark-frontmatter] as well.

## Installation

[npm][]:

```bash
npm install remark-yaml-config
```

## Usage

Say we have the following file, `example.md`:

```markdown
---
remark:
  commonmark: true
  bullet: "*"
---

1)  Commonmark list (this is a parse setting)

*   Hello (this is a stringify setting)
```

And our script, `example.js`, looks as follows:

```javascript
var vfile = require('to-vfile')
var remark = require('remark')
var frontmatter = require('remark-frontmatter')
var yamlConfig = require('remark-yaml-config')

remark()
  .use(frontmatter)
  .use(yamlConfig)
  .process(vfile.readSync('example.md'), function(err, file) {
    if (err) throw err
    console.log(String(file))
  })
```

Now, running `node example` yields:

```markdown
---
remark:
  commonmark: true
  bullet: "*"
---

1.  Commonmark list (this is a parse setting)

*   Hello (this is a stringify setting)
```

## API

### `remark.use(yamlConfig)`

Passes the configuration at the `remark` field as [parse][parse-settings]
and [stringify][stringify-settings] settings to **remark**.

Just like [`remark-comment-config`][remark-comment-config], but YAML is
more visible.

## Related

*   [`remark-comment-config`][remark-comment-config]
    — Configure with comments
*   [`remark-frontmatter`][remark-frontmatter]
    — Frontmatter support, including yaml, toml, and more

## Contribute

See [`contributing.md` in `remarkjs/remark`][contributing] for ways to get
started.

This organisation has a [Code of Conduct][coc].  By interacting with this
repository, organisation, or community you agree to abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/remarkjs/remark-yaml-config.svg

[build]: https://travis-ci.org/remarkjs/remark-yaml-config

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-yaml-config.svg

[coverage]: https://codecov.io/github/remarkjs/remark-yaml-config

[downloads-badge]: https://img.shields.io/npm/dm/remark-yaml-config.svg

[downloads]: https://www.npmjs.com/package/remark-yaml-config

[chat-badge]: https://img.shields.io/badge/join%20the%20community-on%20spectrum-7b16ff.svg

[chat]: https://spectrum.chat/unified/remark

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[license]: license

[author]: https://wooorm.com

[npm]: https://docs.npmjs.com/cli/install

[remark]: https://github.com/remarkjs/remark

[parse-settings]: https://github.com/remarkjs/remark/blob/master/packages/remark-parse/readme.md#options

[stringify-settings]: https://github.com/remarkjs/remark/blob/master/packages/remark-stringify/readme.md#options

[remark-comment-config]: https://github.com/remarkjs/remark-comment-config

[remark-frontmatter]: https://github.com/remarkjs/remark-frontmatter

[contributing]: https://github.com/remarkjs/remark/blob/master/contributing.md

[coc]: https://github.com/remarkjs/remark/blob/master/code-of-conduct.md
