# Community extensions for Tsumihon (unofficial)

**Unofficial source definitions for the Tsumihon app, kept in a separate repository. Contributions are welcome.**

> **This is not an official Tsumihon project.** It is a separate repository: it
> is not part of the app and is not distributed with it through the App Store or
> Google Play. You add it yourself, or you do not. Everything here is provided
> as-is, without any warranty. Use it at your own risk.

[![Add this repository](https://img.shields.io/badge/Add%20this%20repository-1F2937?style=for-the-badge)](https://tsumihon.app/add-repository?url=https%3A%2F%2Fraw.githubusercontent.com%2Ftetsuyomiyazaki%2Ftsumihon-extensions%2Fmain&name=Community%20Extensions%20%28unofficial%29)

<sub>Open the link on the device the app is installed on. The app shows you this
repository's address and asks before it adds anything.</sub>

---

## What this is

Tsumihon comes with **no repository set up, and with none of the sources listed
here**. Without one it catalogues books by hand and imports a book from a link
you paste or share. Searching the sites below needs a repository the user adds
themselves.

This is one such repository. Anyone can publish one: the format is described
below. It is a list of source definitions, each one a small JSON manifest
describing how to search a site and read its metadata. Adding the repository installs nothing on its own; it only lets the app
show you what is available here.

## Adding it

**On a phone or tablet with the app installed**, use the button above. It opens
the app on a confirmation screen.

**By hand**, in the app — Settings → Search Providers → Source Repositories →
Add Repository — paste:

```
https://raw.githubusercontent.com/tetsuyomiyazaki/tsumihon-extensions/main
```

The app also accepts the GitHub shorthand `tetsuyomiyazaki/tsumihon-extensions` and
the repository's web URL, and normalises both to the address above.

## What is in it

### Aggregators

These are marked as mature. The app hides mature sources until you turn on
**Show mature sources** in its source settings.

**If you installed one of these before version 1.3.1 (E-Hentai: 1.4.1):** after
you update it, the app stops searching it and stops running auto-import rules
for it until you turn on **Show mature sources**. The source stays installed and
your login for it is kept.

| Source | Notes |
|---|---|
| **Schale Network** | Multi-mirror archive network with automatic fallback |
| **E-Hentai** | Large archive; supports ExHentai when you supply cookies |
| **nHentai** | Doujinshi and manga aggregator |
| **Hitomi.la** | Gallery search and browsing |
| **Chaika** | Panda archive mirror with comprehensive search |
| **Hdoujin** | Aggregator and archive |
| **Doujinshi.info** | Database with multilingual metadata |

### Reference and ISBN

These look up commercial books rather than doujinshi. NDL Search and openBD
answer ISBN scans; the other two are reference databases.

| Source | Notes |
|---|---|
| **NDL Search** | National Diet Library of Japan — ISBN and book metadata |
| **openBD** | Japan ISBN Agency public database |
| **Media Arts DB** | Agency for Cultural Affairs manga/anime database |
| **MangaUpdates** | Series database — authors, genres, publication status |

### Self-hosted

| Source | Notes |
|---|---|
| **LANraragi** | Your own LANraragi server. Needs a host and an API key |

## Index and manifests

`index.json` lists every published source; each entry points at a manifest file
in this repository (for example [`schale.json`](schale.json)), which holds the
actual source definition. An index entry looks like this:

```jsonc
{
  "id": "schale",
  "name": "Schale Network",
  "description": "Multi-mirror doujinshi archive network with automatic fallback",
  "version": "1.3.1",
  "author": "tetsuyomiyazaki",     // whoever wrote the source
  "icon": "cloud_sync",            // a Material icon name
  "category": "aggregator",        // aggregator | reference | self_hosted
  "mature": true,                  // hidden until "Show mature sources" is on
  "downloadUrl": "https://raw.githubusercontent.com/…/schale.json",
  "visibility": "public"           // public | private | selfhosted
}
```

## Contributing a source

1. Add `<id>.json` with the source definition.
2. Add the matching entry to `index.json`, including `downloadUrl`.
3. Bump `version` on the entry and the manifest together — the app compares them
   to decide whether an update is available.
4. For a source with adult content, set `"mature": true` on the index entry and
   in the manifest.
5. Open a pull request.

Sources that require credentials must not carry any in the manifest. The app
collects them from the user and stores them on device.

## Problems with a source

Open an issue in this repository. Source definitions are maintained here, not in
the app, so this is the place a broken source gets fixed. Please do not send
source problems to Tsumihon app support.

If you operate a site listed here and want its definition removed, open an issue
and it will be taken down.

## Disclaimer

- **Unofficial.** This repository is not an official part of Tsumihon. It is
  separate from the app and is only used when a user adds it.
- **Third-party sites.** Each source describes a third-party website. This
  repository does not operate, host, control or endorse those sites or anything
  on them.
- **No content.** There are no books, images or other media here: only small,
  deliberately readable JSON files that describe how to query a site.
- **Your responsibility.** A repository decides which sites the app talks to, and
  a source decides what it sends them. Read a source before installing it. What
  you install and what you access with it is up to you, and you are responsible
  for following the laws of your country and the terms of the sites you use.
- **No warranty.** Everything is provided as-is. Sources can break or disappear
  at any time.
