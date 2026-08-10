# Vendored third-party assets

Provenance and integrity of every third-party file shipped by this module. When updating a library: replace the file, update this table and the matching `sha256` in [.vendored/package.json](.vendored/package.json), and update [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md) if the upstream license changed.

All files live in `assets/libs/hugo-mod-abcjs/`.

| File | Library | Version | License | SHA-256 |
|---|---|---|---|---|
| `abcjs-basic-min.js` | [abcjs](https://github.com/paulrosen/abcjs) | 6.6.3 | MIT | `abdab74cf95c39fb9ff4ae0c96735b9c35222851f0844ce471ddd4354739bc75` |

Source: `https://cdn.jsdelivr.net/npm/abcjs@6.6.3/dist/abcjs-basic-min.js`

First-party files, under this repository's [LICENSE](LICENSE): `hugo-mod-abcjs.js`, `hugo-mod-abcjs.css`.

## How updates reach us

[.vendored/package.json](.vendored/package.json) pins the same versions as ordinary npm dependencies. Nothing ever installs it. It exists so Dependabot opens a pull request when one of these libraries releases, and so GitHub raises a security alert against the exact code this module serves to readers.

Dependabot can bump that manifest but cannot re-download a minified bundle, so a merged bump would otherwise leave the declared version and the shipped bytes silently out of sync. `scripts/check-vendored.mjs` closes that gap: it fails the build unless the pinned version, this table and the checksum of the committed file all agree.

## Verifying integrity

```bash
node scripts/check-vendored.mjs
sha256sum assets/libs/hugo-mod-abcjs/abcjs-basic-min.js
```
