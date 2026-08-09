# Vendored third-party assets

Provenance and integrity of every third-party file shipped by this module. When updating a library: replace the file, update this table, and update [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md) if the upstream license changed.

All files live in `assets/libs/hugo-mod-abcjs/`.

| File | Library | Version | License | SHA-256 |
|---|---|---|---|---|
| `abcjs-basic-min.js` | [abcjs](https://github.com/paulrosen/abcjs) | 6.6.3 | MIT | `abdab74cf95c39fb9ff4ae0c96735b9c35222851f0844ce471ddd4354739bc75` |

Source: `https://cdn.jsdelivr.net/npm/abcjs@6.6.3/dist/abcjs-basic-min.js`

First-party files, under this repository's [LICENSE](LICENSE): `hugo-mod-abcjs.js`, `hugo-mod-abcjs.css`.

## Verifying integrity

```bash
sha256sum assets/libs/hugo-mod-abcjs/abcjs-basic-min.js
```
