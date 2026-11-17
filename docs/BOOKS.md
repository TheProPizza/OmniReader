# Books, acquisition and e-reader delivery

Open **Books** for an ordinary-book reading list, metadata discovery, imports and series groups. Manga and light novels retain their existing discovery and source readers. Existing prose imports can be moved with **Show in Books**; importing through the general import dialog also offers a Books category.

## Setup

Use **Settings → Books & e-readers** in the localhost browser on the host PC. Phones can read and use configured services; configuration and secret fields are restricted to the PC. Credentials are encrypted in `data/book-integrations/settings.enc` using the separate local key. Back up the entire data folder together; possession of that backup permits decryption.

| Service | Configuration | Behaviour |
| --- | --- | --- |
| Open Library | None | Public metadata search, throttled and cached. |
| Google Books | Books API key | Adds volume metadata and ISBN matches. |
| Hardcover | Account API token | Adds book metadata through its GraphQL search API. |
| Legado book sources | Import trusted text-source JSON files or URLs in Books → Sources | Native search, metadata, chapter reading, source switching and offline chapter downloads. |
| Kindle | SMTP account/app password, sender, Kindle address | Emails retained EPUB originals. Sender must be approved in Amazon's document settings. |
| Kobo / Google Drive | Own Google OAuth app; Kobo folder ID | Connect using the button or an offline refresh token. Uploads original EPUB/PDF files into the linked Rakuten Kobo folder. |
| Kobo / Dropbox | Own Dropbox OAuth app; Kobo folder path | Connect using the button or an offline refresh token. Uploads original EPUB/PDF files into the linked Kobo folder. |

Save credentials before testing connections or starting OAuth. Register the callback URI displayed in Settings in your OAuth app. Google Drive needs access to the existing folder created by Kobo; its connection requests Drive access, but OmniReader only uploads to the configured folder. Dropbox needs full-Dropbox content access with `files.content.write`, because an app-folder-only token cannot reach Kobo's folder. Tokens renew on delivery. Providers may impose testing-app or account restrictions.

## Downloads and reading

Select a metadata result to add to the reading list or find it in imported Legado sources. Source books open with chapters and source switching; no separate application is required. Use Download beside a chapter or Download all to save on this device. Metadata catalogues do not supply a book file. Imported EPUB/PDF files continue to use the existing parser, storage quota and file-hash deduplication.

EPUB chapters use the existing typography, themes, search, bookmarks and revision-based progress system. PDF.js renders one PDF page at a time, with zoom, themes, page navigation, bookmarks and tracked page resumption. PDF fonts are fixed by the document. Reading position sync is between browsers/devices connected to the same OmniReader PC; Kindle/Kobo positions are separate. Local network access still requires the PC to remain running.

**Download** uses the existing browser offline store. iOS offline storage needs a secure context (HTTPS or localhost); ordinary HTTP LAN access supports reading and server progress, but cannot install a service worker. PDFs cache required font/CMap resources after viewing them online. Retained originals can be exported or delivered; old EPUB imports made before originals were retained need re-importing to enable those actions.

## Native Windows acquisition

Legado text-source definitions run inside OmniReader's TypeScript backend, with isolated on-demand rule workers. No external server, Docker or Python is required. See [Native book sources](NATIVE-BOOK-SOURCES.md) for compatibility, licensing and security boundaries.

## Delivery boundaries and advanced Kobo Sync investigation

Kindle email uses TLS and an approved sender. OmniReader limits an EPUB to 34 MiB before MIME encoding and reports mail-provider acceptance; Amazon can still require verification or reject a document. It never reports that mail acceptance proves delivery on the device. An interrupted send is marked uncertain rather than sent automatically again.

Kobo's supported cloud workflows require a compatible device model, a linked account and a device sync after upload. Google Drive uses a resumable upload session restricted to Google's API host; Dropbox uploads to the configured path without overwriting an existing book.

Advanced Kobo Sync is a separate device protocol. Calibre-Web's implementation requires replacing `api_endpoint` in the Kobo configuration, maintaining device-specific sync tokens and optionally proxying store requests. Its documented limitations include large-library timeouts and no PDF sync. Adding that protocol directly would introduce a second library/sync server and require testing on physical Kobo firmware. This update therefore uses Kobo's supported Drive/Dropbox delivery and does not change device settings or claim Kobo reading-position sync.

## Architecture and verified API references

Ordinary books add optional `Title.book` metadata while retaining the prose reader. Existing library, status, collections, history, bookmarks, progress conflicts and browser download storage remain authoritative. Migration 009 retains original-file records and e-reader delivery jobs; migration 010 adds Legado source/book/chapter/media tables. Source management is under `server/legado/`; metadata, encrypted service credentials and delivery remain under `server/books/`. Source definitions/headers remain in the private local database and are not exposed by public source summaries. PDF.js assets are packaged for the browser.

- [Hardcover API](https://docs.hardcover.app/api/getting-started/), [Google Books volumes](https://developers.google.com/books/docs/v1/using), [Open Library search](https://openlibrary.org/dev/docs/api/search).
- [Amazon Send to Kindle email](https://www.amazon.com/sendtokindle/email).
- [Kobo Google Drive](https://help.kobo.com/hc/en-us/articles/15335985512983-Add-books-to-your-eReader-using-Google-Drive), [Kobo Dropbox](https://help.kobo.com/hc/en-us/articles/360033830114-Add-books-to-your-eReader-using-Dropbox).
- [Google Drive uploads](https://developers.google.com/workspace/drive/api/guides/manage-uploads), [Dropbox OAuth](https://developers.dropbox.com/oauth-guide).
- [Calibre-Web Kobo integration](https://github.com/janeczku/calibre-web/wiki/Kobo-Integration).
