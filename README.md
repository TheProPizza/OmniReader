# OmniReader

**Version 2.2.34** · A local-first reader for manga, manhwa, manhua, light novels and imported books. OmniReader runs on your Windows PC and opens in your browser, with optional access from your phone.

## Download and start

1. Get a Windows ZIP from the **[public releases page](https://github.com/TheProPizza/OmniReader/releases)**. Stable Windows packages are mirrored from the private build workflow.
2. Extract the **whole ZIP** to a folder you want to keep.
3. Open **Start OmniReader**. On first launch, keep your internet connection on while OmniReader prepares its reading engines and sources. You do not need to install Node.js or Java yourself.
4. Open **Stop OmniReader** when you want to shut it down.

You don't need an OmniReader account. Your library is stored on your own PC.

> **Important:** GitHub's **Code → Download ZIP** is the source code, not the ready-to-run Windows download.

## What you can do

- **Discover stories:** Browse MangaBaka, AniList or MyAnimeList rankings. Each shelf starts with **two rows**; **View more** adds another two rows without leaving Discover.
- **Find chapters:** Search your enabled comic sources, including MangaDot and Comix, or manage light-novel sources through the LNReader catalogue in **Sources**. Individual websites and extensions can occasionally be unavailable.
- **Read your way:** Comic reading modes, a configurable novel reader, bookmarks, reading progress and offline downloads.
- **Manage your library:** Save favourites, track reading status, import supported books and comics, and see your history under **My library**.
- **Sync with AniList:** Optionally connect AniList in Settings to match titles and sync supported reading progress.

## Updates and keeping your library

On the **Windows host PC**, open **Settings → Application updates → Check for updates → Download & install**. The updater checks the [public releases](https://github.com/TheProPizza/OmniReader/releases) for a newer **stable** version, verifies the Windows ZIP and restarts the app. Phone browsers cannot install updates.

Stable Windows releases are **mirrored automatically to the public repository** after the private package is published and checked. The public release must be published as a regular release, tagged to match its application version, with an asset named `OmniReader-Windows.zip`. Drafts and prereleases are not offered through the updater.

For a manual upgrade, stop OmniReader and replace the application files from the new ZIP. **Keep your entire `data/` folder and any `.env` file**. They contain your library, downloads, reading progress and configuration. Do not overwrite them with a fresh installation.

## Read on your phone

In **Settings → Phone Access** on your PC, choose:

- **Local Access:** Connect from a phone on the same trusted home network using the provided link or QR code. If Windows asks about firewall access, allow **Private networks only**.
- **Remote Access:** Connect away from home through an optional, email-protected Cloudflare Quick Tunnel. Approve the email addresses in Settings and use the current HTTPS link or QR code. Links are temporary and can change when the tunnel restarts.

**Your PC must stay running** for either option. Phone Access is off by default. Do not forward OmniReader's port on your router.

## Need help?

If the app won't start, check `data/launcher.log`. For comic engine problems, open **Sources** and use the restart or startup-report options. A particular reading source may be down even when OmniReader itself is working.

For developers, more documentation is available in the source repository under `docs/` (not included in the Windows ZIP).

Licensed under [MIT](LICENSE). Third-party components retain their respective licences.
