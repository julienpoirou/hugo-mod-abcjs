# Vendored third-party assets

Provenance and integrity of every third-party file shipped by this module.
When updating a library, replace the file, update this table, and update
`THIRD_PARTY_LICENSES.md` if the upstream license changed.

| File | Library | Version | Source | License | SHA-256 |
|---|---|---|---|---|---|
| `assets/libs/hugo-mod-abcjs/abcjs-basic-min.js` | [abcjs](https://github.com/paulrosen/abcjs) | 6.6.3 | `https://cdn.jsdelivr.net/npm/abcjs@6.6.3/dist/abcjs-basic-min.js` | MIT | `abdab74cf95c39fb9ff4ae0c96735b9c35222851f0844ce471ddd4354739bc75` |

First-party files (not covered above): `assets/libs/hugo-mod-abcjs/hugo-mod-abcjs.js`,
`assets/libs/hugo-mod-abcjs/hugo-mod-abcjs.css` — licensed under this
repository's [LICENSE](LICENSE).

## Verifying integrity

```bash
sha256sum assets/libs/hugo-mod-abcjs/abcjs-basic-min.js
```
