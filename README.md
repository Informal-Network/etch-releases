# Etch releases

Public release files for the **Etch** desktop app — signed installers and the updater feed.

The source code lives in the private `Informal-Network/etch-app` repository. This
repository holds release assets only; nothing here is built from this repo, and no
source archive is ever mirrored.

- Update feed: `releases/latest/download/update.json`
- Every asset is listed in `SHA256SUMS`; each updater payload ships with its
  `.sig` minisign signature.

## Release policy

Releases follow the [continuous canary policy](docs/RELEASE-POLICY.md): etch-app
mirrors each release here as soon as it is cut, and nothing waits for a time
gate. The update channel rolls each release out in stages.
