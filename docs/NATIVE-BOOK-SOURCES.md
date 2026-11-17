# Native Legado book sources

Open **Books → Sources** on the PC and import a Legado JSON file or a public JSON URL. A file may contain one source object or an array (up to 200 sources / 4 MB). Import only sources you trust. Re-import the same source address to update its rules; enable, disable or remove sources here. Updating/removing a source preserves library entries, saved chapters and progress. No source list is installed automatically.

**Books → Discover books → All book sources** searches enabled sources concurrently, with per-source errors. Choose a source in the search selector to search it alone. Book catalogue searches remain available through Open Library, Google Books and Hardcover; catalogue records do not include book text. A catalogue book's **Find a reading source** searches the imported sources without leaving OmniReader.

A source book opens in the native Books detail page with metadata, chapters, reading controls and **Change reading source**. Selecting a matching edition links it to the current library entry. Exact title/author evidence also prevents duplicate library entries when opening another source directly. Progress is retained; if chapter names differ between editions, choose the matching chapter explicitly. Source URLs and book/chapter URLs determine stable IDs rather than changing display names.

## Implementation and licensing investigation

Reviewed on 17 November 2026:

- [Legado](https://github.com/LegadoTeam/legado/tree/330e606c4d57e08adc056ff8ab7a4132c784da9a): source JSON entities, search/book-info/TOC/content schemas, rule documentation and Android-specific execution requirements. Its application licence is GPLv3.
- [legado-rule](https://github.com/LegadoTeam/legado-rule/tree/c3e611dd5872bc53ecd81b4ba5f61c92a588a066): parser stages, selector/operator scope, dependencies and JavaScript evaluation. Its README/package metadata advertises MIT, but its checked-in LICENSE identifies PolyForm Internal Use and expressly prohibits distribution. The footer also references a different PolyForm licence. Its JS selector uses host `new Function`.

Neither repository's implementation is copied or bundled. The licence conflict prevents safely treating legado-rule as an MIT dependency, and host JavaScript evaluation is unsuitable for untrusted source definitions. OmniReader implements an independent adapter for the source JSON format. Existing Cheerio, QuickJS, network bounds, scheduler, cookies, library/progress and offline facilities are reused; the only added parser dependencies are MIT-licensed `@xmldom/xmldom` and `xpath`.

- `server/legado/schema.ts`: import validation and compatibility summaries.
- `server/legado/index.ts`: source persistence, provider API, caches, scheduling, media proxy and network bridge.
- `server/legado/worker.mjs`: independent rule interpreter and isolated JavaScript VM.
- Migration 010 adds separate source/book/chapter/media tables; Keiyoushi and LNReader tables are unchanged.
- Books acquisition adapters from the previous integration are removed. Obsolete acquisition jobs are retired and their payloads cleared; encrypted settings migration removes old acquisition credentials. Completed imported originals, metadata-provider credentials and e-reader delivery settings are preserved.

## Practical compatibility

Supported for **text sources (`bookSourceType: 0`)**:

| Feature | Support |
| --- | --- |
| Imports | Current Legado JSON, including rule objects encoded as JSON strings; source groups/order/enabled state |
| HTML | CSS and common legacy `class.`, `id.`, `tag.`, chained selectors, numeric indexes/exclusions; text, own text, HTML and common attributes |
| XPath | XPath 1.0 through a bounded DOM parser |
| JSONPath | Properties, bracket properties, array indexes/unions/slices, wildcards, recursive traversal and sandboxed predicate filters |
| Composition | `&&` concatenation, `||` fallback, `%%` interleaving, `##` regex replacement, inline `{{…}}`, `@put`/`@get` variables |
| JavaScript | `@js:`, whole `<js>…</js>` blocks, inline `jsLib`, result transformations, `result`, `baseUrl`, `key`, `page`, book/chapter context |
| Helpers | String/element selection, basic element text/HTML/attribute/select helpers, synchronous `java.ajax`/`connect`, get/put variables, URL encoding, base64, MD5 and SHA-256 |
| Requests | Relative/public HTTP(S) URLs, GET/POST/HEAD, JSON request options, source headers, response charset decoding (including GBK), isolated per-operation cookies |
| Reading | Search/book metadata, paginated TOCs (50 pages / 20,000 chapters), chapter pagination (12 pages), sanitized text/illustrations, restricted-chapter flags |
| Reliability | Two concurrent source operations, request pacing, bounded queue, short search cache, duplicate-page detection, one transient GET retry, bounded failures and persistent chapter cache |

This is **not complete Android Legado compatibility**. Android/Rhino Java classes, arbitrary imports, WebView/browser automation, interactive login UI, remote jsLib URLs, arbitrary filesystem/network access, Java crypto libraries, image decryption, payment actions, audio/video/image/file-only sources, batch-content APIs, complex legacy index syntax, JSoup's full Java object API and JavaScript Promise-based rules are not implemented. UTF-8 is used for outbound search text; sources requiring legacy-charset request encoding may need adapted rules. Exploration feeds, live source subscriptions/automatic remote code updates and editor/debugger features are outside this adapter. Some source fields are imported but ignored, including auxiliary book-info fields. Compatibility warnings are shown for known Android requirements; execution errors remain visible rather than silently executing unsupported helpers.

Source requests are restricted to the declared source origin and any literal alternate search origin. Sources that redirect to other websites require an updated definition; image hosts may differ but receive no source headers. Nonstandard ports and credentials embedded in URLs are refused. Use HTTPS for source credentials. Cookie jars last for an operation, so sources that require a persistent logged-in browser session may not work. A working rule cannot guarantee a website is available or accepts automated requests.

## Security and resource bounds

JavaScript runs in a QuickJS WASM VM inside a disposable worker, never `eval`, `new Function` or Node's VM in the server realm. Workers cannot obtain Node globals through the JSON-only host bridge. Java/Android imports fail explicitly. VM memory/stack/instruction limits, worker memory limits, parser watchdogs, a 55-second operation deadline and bounded request/response budgets constrain infinite JS, pathological regex/selectors and oversized output. Workers run only on demand and terminate after each operation; no idle browser, service, GPU or extra application is required.

The parent validates each HTTP request, method, body, header and origin, applies per-source pacing and pins validated public DNS addresses to direct and proxy connections. Loopback/private/link-local/reserved destinations and unsafe redirects are rejected. Only the source's own headers/cookies are used; app cookies, metadata keys and delivery credentials are never passed to rules. Public HTTP is supported without authentication headers; do not put private credentials in HTTP request bodies or URLs. Rule definitions and source credentials are private local database data: public source summaries omit rules/headers and redact URL paths/query strings. Protect data-folder backups accordingly.

Chapters are sanitized before caching and rendering. Images use validated local media IDs; scripts, event handlers, external navigation and unsafe images are removed. Raw source responses are never rendered as executable pages.

## Offline reading and migration

Use **Download** beside a chapter or **Download all** on a book. This reuses the browser's existing download records, quota checks, asset cache and atomic completion logic. Completed chapters also remain in the PC's persistent chapter cache; disabling/removing a source does not erase them. Browser downloads are visible under **Offline downloads**. Failed/incomplete browser downloads can be retried; a bulk operation stops when its page closes and can be continued for the remaining chapters. This chapter-based workflow does not synthesize an EPUB/PDF or deliver source chapters to Kindle/Kobo. Imported EPUB/PDF originals and their delivery controls remain available.

iOS offline Cache Storage/service workers require HTTPS or localhost. HTTP LAN reading and server progress work normally, but an insecure LAN origin cannot save offline chapters on iOS. Progress/bookmarks continue to sync through the existing OmniReader account and server when connected.

Essential verification covers file/URL import, CSS/legacy selectors, JSONPath, XPath, sandboxed JS, chapter/TOC pagination, private URL/redirect rejection, execution limits, sanitized content, cached/offline reading, source updates/switching, stable identities and progress preservation. Representative fixtures establish adapter behavior, not universal compatibility with third-party source lists.

A live public-page probe in the managed development environment returned HTTP 403 through the DNS-pinned proxy path, while its normal hostname proxy path returned 200. Private-network protection was retained; no unvalidated proxy fallback was added. Fixture and browser checks passed, but live third-party source operation on the target Windows connection is not established by those checks. Some proxy services route IP-address CONNECT requests differently from hostname CONNECT requests; use a compatible connection rather than disabling address validation.
