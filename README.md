# hugo-mod-abcjs

[![CI](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/ci.yml)
[![CodeQL](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/codeql.yml/badge.svg)](https://github.com/julienpoirou/hugo-mod-abcjs/actions/workflows/codeql.yml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/julienpoirou/hugo-mod-abcjs/badge)](https://scorecard.dev/viewer/?uri=github.com/julienpoirou/hugo-mod-abcjs)
[![Release](https://img.shields.io/github/v/release/julienpoirou/hugo-mod-abcjs?include_prereleases&sort=semver)](https://github.com/julienpoirou/hugo-mod-abcjs/releases)
[![Hugo Module](https://img.shields.io/badge/Hugo-Module-FF4088?logo=hugo&logoColor=white)](https://gohugo.io/hugo-modules/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

<p align="center">
  <img src="./logo.svg" alt="hugo-mod-abcjs logo" width="160" height="160">
</p>

<p align="center">
  <strong>ABC music notation in your Hugo pages.</strong><br>
  One shortcode, vendored <code>ABCjs</code>, responsive SVG rendered in the reader's browser.
</p>

## Requires

- Hugo >= `0.124`. The extended edition is not required.

## Install

**Binary** - Hugo and Go installed locally:

```bash
hugo mod init example.com/my-site
hugo mod get github.com/julienpoirou/hugo-mod-abcjs
```

```toml
# hugo.toml
[module]
  [[module.imports]]
    path = "github.com/julienpoirou/hugo-mod-abcjs"
```

**Container** - Docker installed locally:

```bash
alias hugo='docker run --rm -v "$PWD":/src -p 1313:1313 hugomods/hugo:go-git hugo'
hugo mod init example.com/my-site
hugo mod get github.com/julienpoirou/hugo-mod-abcjs
```

## Usage

**Shortcode** - Raw ABC option between the tags:

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

**Self-closing shortcode** - Source read from a file:

```text
{{< abcjs src="renderers/abc.abc" />}}
```

**Self-closing shortcode** - Source passed as base64:

```text
{{< abcjs b64="WDoxClQ6U2NhbGUKSzpDCkMgRCBFIEYgfA==" />}}
```

### Parameters

| Param | Description |
|---|---|
| inner content | Raw ABC source between the opening and closing tags |
| `src` | Path, relative to `assets/`, of a file holding the ABC source |
| `b64` | Base64-encoded ABC source |

> At least one input is required. If several are given, `b64` wins over `src`, and `src` wins over the inner content the others are ignored silently.

> A missing or empty source fails the build with an explicit error rather than emitting a blank page. An invalid `b64` payload is not caught at build time: it surfaces at render time, as an error message in place of the score.

> `src` is resolved with `readFile` from the project root, so the file must live in your own site's `assets/`. A `.abc` mounted from a theme or from another module will not be found.

## Rendering

The score is drawn in the reader's browser as a responsive `<svg>` that reflows with its container.

- The stylesheet and both scripts are injected once per page, at the first `abcjs` shortcode in the flow of the content, not in `<head>`. Each one is fingerprinted and carries a Subresource Integrity hash.
- ABCjs runs with `responsive: "resize"` and nothing else. Scale, transposition and staff width are not configurable yet.
- Without JavaScript the shortcode leaves an empty block: there is no server-side fallback.

## Vendored assets

ABCjs `6.6.3` ships inside the module, no CDN, no third-party request at page load. Provenance, license and SHA-256 are recorded in [VENDORED.md](VENDORED.md).

## License

MIT © 2025 [Julien Poirou](mailto:julienpoirou@protonmail.com)
