<div align="center">

<img src="https://tsumihon.app/favicon.png" width="72" alt="" />

# Tsumihon Extensions

**The source repository for [Tsumihon](https://tsumihon.app), a collection manager for the doujinshi and manga you already own.**

[![Add to Tsumihon](https://img.shields.io/badge/Add%20to%20Tsumihon-3B82F6?style=for-the-badge&logo=bookstack&logoColor=white)](https://tsumihon.app/add-repository?url=https%3A%2F%2Fraw.githubusercontent.com%2Ftetsuyomiyazaki%2Ftsumihon-extensions%2Fmain&name=Tsumihon%20Extensions)
&nbsp;
[![Documentation](https://img.shields.io/badge/Docs-1F2937?style=for-the-badge&logoColor=white)](https://tsumihon.app/docs)
&nbsp;
[![Support](https://img.shields.io/badge/Support-1F2937?style=for-the-badge&logoColor=white)](https://tsumihon.app/support)

<sub>Tap **Add to Tsumihon** on the device the app is installed on.<br />
It opens Tsumihon directly, shows you this address, and asks before adding anything.</sub>

</div>

---

## What this is

Tsumihon ships with **no sources and no repository**. A fresh install can
catalogue books by hand and scan ISBNs, and that is all it can do until you
point it at a repository yourself.

This is that repository. It is a list of source definitions — each one a small
JSON manifest describing how to search a site and read its metadata. Adding the
repository installs nothing on its own; it just lets the app show you what is
available.

## Adding it

**On a phone or tablet with Tsumihon installed**, use the button above. It opens
the app on a confirmation screen.

**By hand**, in the app — Settings → Search Providers → Extensions → Add
repository — paste:

```
https://raw.githubusercontent.com/tetsuyomiyazaki/tsumihon-extensions/main
```

The app also accepts the GitHub shorthand `tetsuyomiyazaki/tsumihon-extensions` and
the repository's web URL, and normalises both to the address above.

## What is in it

### Aggregators

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

These look up commercial books rather than doujinshi, and are what the ISBN
scanner talks to.

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

## Manifest format

`index.json` lists every published source; each entry points at a manifest file
in this repository.

```jsonc
{
  "id": "schale",
  "name": "Schale Network",
  "description": "Multi-mirror doujinshi archive network with automatic fallback",
  "version": "1.2.0",
  "author": "Tsumihon",
  "icon": "cloud_sync",            // a Material icon name
  "category": "aggregator",        // aggregator | reference | self_hosted
  "downloadUrl": "https://raw.githubusercontent.com/…/schale.json",
  "appStoreSafe": true,
  "visibility": "public"           // public | private | selfhosted
}
```

## Contributing a source

1. Add `<id>.json` with the source definition.
2. Add the matching entry to `index.json`, including `downloadUrl`.
3. Bump `version` on the entry and the manifest together — the app compares them
   to decide whether an update is available.
4. Open a pull request.

Sources that require credentials must not carry any in the manifest. The app
collects them from the user and stores them on device.

## A note on what you install

A repository decides which sites the app talks to, and a source decides what it
sends them. Add repositories you trust, and read a source before installing it —
they are small, deliberately readable JSON files, and that is the point.

You are responsible for following the laws of your own country.

## Licence

The manifests in this repository are provided as-is. Each source describes a
third-party website that this project does not operate, endorse, or host content
for.
