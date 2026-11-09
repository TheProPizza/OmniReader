# OmniReader

**One library for manga, manhwa, manhua and light novels.**

OmniReader is a self-hosted reader for Windows with a browser-based interface. Discover titles, choose reading sources, organise your library and pick up where you left off. You can also read from a phone or tablet while OmniReader is running on your PC.

> [!IMPORTANT]
> **Public beta:** OmniReader is still in active development. Some sources, features and mobile workflows may be unreliable. Back up your library before upgrading.

**[Download OmniReader for Windows](https://github.com/TheProPizza/OmniReader/releases)** · [Current beta: v2.2.29](https://github.com/TheProPizza/OmniReader/releases/tag/v2.2.29) · [Report a bug](https://github.com/TheProPizza/OmniReader/issues)

## Features

- **Read comics and light novels:** manga, manhwa, manhua and web/light novels in one place.
- **Discover series:** title information and recommendations using MangaBaka, with AniList and MyAnimeList as alternatives or fallbacks.
- **Choose your sources:** browse supported comic extensions and LNReader novel sources, with source management in the app.
- **Keep your place:** a local library, reading history, chapter progress and reading preferences.
- **Customise reading:** page and vertical reading modes, sizing controls and reader preferences.
- **Bring your own files:** import supported locally stored books and comics.
- **Optional AniList sync:** connect your AniList account to track reading activity.
- **Read on other devices:** access the same library on your home network or through an optional protected remote connection.

Source availability depends on third-party websites and extensions. Not every Android-dependent extension works in the Windows runtime.

## Download and install (Windows)

**Requirements:** 64-bit Windows and an internet connection for the initial setup. You do **not** need to install Node.js or Java manually.

1. Open the [Releases page](https://github.com/TheProPizza/OmniReader/releases).
2. Under the newest available release, expand **Assets** and download the file named like `OmniReader-v2.2.29-Windows.zip`.
3. **Extract the entire ZIP** to a permanent folder you can keep (for example, inside Documents). Don't run it from inside the compressed ZIP.
4. Double-click **`Start OmniReader.vbs`** in the extracted folder.
5. Wait for the first-time setup to finish. OmniReader will download and prepare its runtime and reading sources; this can take several minutes.
6. The reader opens in your default browser. Use **`Stop OmniReader.vbs`** when you want to shut it down.

The Windows ZIP is the runnable release. GitHub's green **Code → Download ZIP** button downloads this *repository*, not the Windows application.

## Getting started

1. Open **Sources** to find and manage comic and light-novel sources.
2. Browse or search for a series, then choose an available source to read it.
3. Add titles to **My library** to keep your progress and reading history together.
4. Open **Settings** to adjust your reader, manage AniList integration or enable phone access.

OmniReader stores its local library and settings on your computer. An OmniReader sign-in account is not required.

## Read on your phone or tablet

On your Windows PC, open **Settings → Phone Access**. Access is **off by default**.

| Mode | How it works | What you need |
| --- | --- | --- |
| **Local Access** | Enables a local link and QR code to open OmniReader from a browser on the same home network. | Your phone/tablet on the same trusted network as your PC. |
| **Remote Access** | Creates a temporary HTTPS link through Cloudflare Tunnel, protected by email verification for approved addresses. | An internet connection and an approved email address. |

Both modes require the **Windows PC to stay powered on, online and running OmniReader**. Remote URLs can change after a restart. You don't need to forward ports on your router.

Use Safari or Chrome on your phone; where supported, you can add the site to your home screen. Only enable local access on a network you trust, and never share email verification codes.

## Updating without losing your library

There is no in-app one-click updater in this beta. Until one is available:

1. Run **`Stop OmniReader.vbs`**.
2. **Back up your existing `data` folder** before changing anything. Keep any private `.env` configuration you created, too.
3. Download and extract the new Windows ZIP into a new folder.
4. Move a **copy** of your backed-up `data` folder (and `.env`, if used) into the corresponding locations in the new installation. Do not replace them with an empty folder.
5. Start the new version and check that your library and progress are present before removing the older installation.

The `data` folder contains local application state and should **never** be published or shared in bug reports.

## Troubleshooting

| Problem | What to try |
| --- | --- |
| First launch takes a long time | Leave the setup running and check your internet connection; runtime and source downloads happen on first use. |
| OmniReader doesn't open | Try **Start OmniReader** again and check `data/launcher.log` for errors. |
| A title or chapter won't load | Try another source. Websites and extensions can change or become unavailable independently of OmniReader. |
| Phone can't connect locally | Check that the PC and phone are on the same non-guest home network. A Windows Firewall prompt should be allowed for **Private** networks only. |
| Remote link stopped working | Open **Settings → Phone Access** on the PC and check or regenerate the current link. Temporary tunnel URLs are not permanent. |

If the issue persists, [open a GitHub issue](https://github.com/TheProPizza/OmniReader/issues/new) with your Windows version, OmniReader version, what happened and steps to reproduce it. **Remove personal information, private URLs, email addresses and tokens from logs or screenshots before posting.**

## Current limitations

- **Beta software:** bugs and breaking changes are possible.
- **Windows hosts the reader:** phone and browser access do not run independently of the PC.
- **Third-party sources vary:** some sites may block requests, remove chapters or require a login; some extensions are incompatible.
- **Remote Access uses a temporary tunnel:** it is not intended to provide a permanent hosted service.
- **Updates are manual for now:** an in-app updater is planned, but is not part of v2.2.29.

## Releases, source and attribution

This repository is the **public download and release page** for OmniReader. The application ZIP includes the files needed to run the Windows version, while ongoing development takes place separately.

OmniReader interacts with independent metadata providers, reading sources and extension projects. It is not affiliated with those services. Respect applicable copyright and the terms of any sources you use.

OmniReader's original code is licensed under the [MIT License](LICENSE) (© 2026 TheProPizza). Bundled third-party components retain their own copyright and licence notices; the MIT licence does not replace those separate terms.

---

*Built by [TheProPizza](https://github.com/TheProPizza). Feedback and bug reports are welcome while OmniReader is in beta.*
