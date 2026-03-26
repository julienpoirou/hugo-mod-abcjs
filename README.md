# hugo-mod-abcjs

[![CI](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/ci.yml)
[![CodeQL](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/codeql.yml/badge.svg)](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/codeql.yml)
[![Release](https://img.shields.io/github/v/release/julienpoirou/hugo-mod-abcjs?include_prereleases&sort=semver)](https://github.com/julienpoirou/hugo-mod-abcjs/releases)
[![Hugo Module](https://img.shields.io/badge/Hugo-Module-FF4088?logo=hugo&logoColor=white)](https://gohugo.io/hugo-modules/)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196.svg)](https://www.conventionalcommits.org)

<p align="center">
  <img src="./logo.svg" alt="hugo-mod-abcjs logo" width="160" height="160">
</p>

Standalone Hugo module for ABC music notation rendering with vendored `ABCjs` assets and shortcode helpers.

## Features

- Render scores with `{{< abcjs >}}`
- Support `src`, `b64`, and inline body input modes
- Ship vendored `ABCjs`
- Render responsive SVG output in the browser
- Fail explicitly at build time when shortcode source is missing

## Requirements

- Hugo `>= 0.124`
- A Hugo site with Hugo Modules enabled

## Installation

Import the module in your Hugo site:

```toml
[module]
  [[module.imports]]
    path = "github.com/julienpoirou/hugo-mod-abcjs"
```

## Usage

Inline source:

```text
{{< abcjs >}}
X:1
T:Scale
M:4/4
L:1/4
K:C
C D E F | G A B c |
{{< /abcjs >}}
```

File source:

```text
{{< abcjs src="renderers/abc.abc" />}}
```

## Output assets

The module publishes:

- `vendor/hugo-mod-abcjs/abcjs-basic-min.js`
- `vendor/hugo-mod-abcjs/hugo-mod-abcjs.js`
- `vendor/hugo-mod-abcjs/hugo-mod-abcjs.css`

## Development

```bash
git clone https://github.com/julienpoirou/hugo-mod-abcjs
cd hugo-mod-abcjs
```

The main verification is handled by GitHub Actions with a minimal Hugo site that mounts the module and builds a sample page.

## Contributing

- Use Conventional Commits for branch history
- Update docs or changelog when behavior changes
- Keep sample ABC snippets valid and minimal
- See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md) for contribution guidance
