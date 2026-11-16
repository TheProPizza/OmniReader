# OmniReader changelog

User-facing changes, newest first. Current Windows downloads are on the [public releases page](https://github.com/TheProPizza/OmniReader/releases).

History was reconstructed from versioned source, packaged-download documentation and release commits. Older dates identify when changes were recorded; they are not all independently verified publication dates. Early versions include development snapshots. Missing version numbers have no sufficiently clear surviving notes and are intentionally omitted. Historical remote-access features are no longer available as of v2.2.50.

## Unreleased

<!-- Add public, user-facing notes here before changing the version. -->

## [2.2.57] - 2026-11-16

- Give dropdown arrows consistent inset spacing and reserve room for labels across the app in Liquid Glass and Classic.
- Load more Discover results as you scroll, keeping earlier titles visible and resetting the feed when filters change.
- Keep cover-image traffic separate from the main API rate limit and share library data with search suggestions to prevent redundant library requests.
- Allow saved reading to reopen offline without waiting for online source-setup checks.

## [2.2.56] - 2026-11-16

- Redesign title details as a compact artwork card with prominent reading controls, integrated source choices and expandable descriptions.
- Bring chapters higher up with a combined heading and Download all control, tighter chapter rows and responsive layouts for Liquid Glass and Classic.

## [2.2.55] - 2026-11-16

- Unify live search suggestions across Home, Discover and the sidebar, with cover previews, alternate names, recent searches and keyboard navigation.
- Load catalogue suggestions independently, reuse recent matches while typing, and preserve local-library suggestions when online catalogues are unavailable.
- Improve exact-title and prefix ranking, tolerate small typing and spacing errors, and combine duplicate suggestions while keeping distinct works separate.
- Cancel abandoned catalogue requests without interrupting other browsers, honour suggestion-cache expiry, and preserve title details and keyboard selection as results update.

## [2.2.54] - 2026-11-16

- Add per-chapter offline download buttons and Download all, with saved indicators, queue progress and stop-after-current controls.
- Enable offline saving for readable comic extension chapters while retaining restrictions for other sources.

## [2.2.53] - 2026-11-15

- Integrate Genre with the browsing filters, preserving category selection and resetting pagination when the genre changes.
- Add the full release history directly to Settings → Application updates, with expandable versions and a compact scrolling history.
- Preserve and synchronise the historical changelog and require release notes for future updates.

## [2.2.52] - 2026-11-15

- Compact Phone Access with the QR code beside connection controls.
- Make AniList Connect open one-time, localhost-only application setup instead of remaining disabled when unconfigured.
- Add Discover genres including Isekai, High Fantasy and Sci-Fi, with category and pagination support.
- Increase Liquid Glass transparency slightly and show optional, faded title artwork from the matched work or its anime adaptation.

## [2.2.51] - 2026-11-15

- Remove duplicate mobile search bars and align the six bottom tabs above the iPhone safe area.
- Style dropdowns consistently with Liquid Glass while preserving Classic.
- Automatically try working comic sources in priority order after image or chapter failures, with chapter matching, relative progress transfer and loop protection.

## [2.2.50] - 2026-11-15

- Add Liquid Glass as the default interface with a saved Classic option.
- Add suggested, popular, top-rated and format-based Home shelves.
- Remove Remote Access and its tunnel/session code, keeping Local Access.
- Allow more time for updater preparation and catalogue fallbacks
-  prevent old offline preference writes from replacing newer online changes.

## [2.2.49] - 2026-11-12

- Restore separate Home and Discover pages.

## [2.2.48] - 2026-11-12

- Refresh the updating tab after installation and clear stale interface/update prompts.

## [2.2.47] - 2026-11-12

- Improve duplicate catalogue-card grouping and recovery of the then-supported remote tunnel.

## [2.2.46] - 2026-11-12

- Replace the Windows update installer with a Node helper.

## [2.2.45] - 2026-11-09

- Remove the import-books banner from Home.

## [2.2.44] - 2026-11-09

- Fix the Windows updater working directory.

## [2.2.43] - 2026-11-09

- Temporarily combine Home and Browse and improve exact-title search. Separate pages return in v2.2.49.

## [2.2.41] - 2026-11-09

- Wait for installer readiness before closing the running app.

## [2.2.39] - 2026-11-09

- Handle public tunnel hosts consistently for the then-supported Remote Access feature.

## [2.2.38] - 2026-11-09

- Improve search, cover loading and setup feedback.
- Synchronise the public README, retain the five newest public releases and limit private Actions history to 24 hours.

## [2.2.34] - 2026-11-09

- Improve update recovery and show installation progress.
- Mirror verified Windows packages to the public download repository.

## [2.2.32] - 2026-11-09

- Expand ranking shelves by two rows with View more.

## [2.2.31] - 2026-11-09

- Add the in-app Windows updater, verified downloads, safe extraction and rollback.
- Automate Windows releases through GitHub Releases and include the README and licence in packages.

## [2.2.30] - 2026-11-09

- Improve cross-source and catalogue duplicate grouping while keeping sequels and spinoffs separate.

## [2.2.29] - 2026-11-09

- Add first-launch setup progress and cleaner search results, source chips, diagnostics and format tabs.
- Refresh the Windows package and download guidance.

## [2.2.28] - 2026-11-09

- Use MangaBaka-first metadata with AniList/MyAnimeList fallbacks and improve source-matching reliability.

## [2.2.26] - 2026-11-08

- Improve exact/alternate-title matching and opening valid reading editions.
- Prepare MangaDot, Comix, MangaFire and Atsumaru as preferred comic sources.
- Stop installing Free Web Novel by default while preserving existing installations and progress.

## [2.2.25] - 2026-11-08

- Improve search cancellation, retries, source preference, deduplication, ranking and language selection.

## [2.2.24] - 2026-11-08

- Improve unified search accuracy and source selection.

## [2.2.23] - 2026-11-08

- Fix offline-data handling, shared-source permissions, chapter identities, linked progress and launcher issues.

## [2.2.22] - 2026-11-08

- Try alternate catalogue titles when the initial edition search finds no match.

## [2.2.21] - 2026-11-08

- Filter unrelated predictive results and rank title/alias matches.

## [2.2.20] - 2026-11-08

- Align the sidebar logo, name and collapse control.

## [2.2.19] - 2026-11-08

- Preserve prolonged tunnel protocol negotiation, correct internal host labels and improve connection errors.

## [2.2.18] - 2026-11-08

- Open title pages immediately while sources load and combine search results into one list.

## [2.2.17] - 2026-11-07

- Bound edition-matching waits, add catalogue matches to search and improve suggestions.

## [2.2.16] - 2026-11-07

- Improve tunnel verification, retry backoff, protocol selection and process recovery.

## [2.2.15] - 2026-11-07

- Use AniList implicit OAuth with encrypted, browser-specific connections.

## [2.2.14] - 2026-11-07

- Move Device storage into Settings and remove the profile widget.

## [2.2.13] - 2026-11-07

- Put the AniList colour theme first.

## [2.2.12] - 2026-11-07

- Default new comic preferences to right-to-left reading.

## [2.2.11] - 2026-11-07

- Make Phone Access more compact.

## [2.2.10] - 2026-11-07

- Speed up edition searches with concurrent source requests and short reuse of successful results.

## [2.2.9] - 2026-11-07

- Simplify rating badges.

## [2.2.8] - 2026-11-07

- Remove the sidebar profile display.

## [2.2.7] - 2026-11-07

- Add Home title suggestions and remove the greeting.

## [2.2.6] - 2026-11-07

- Remove the outdated account-sync card.

## [2.2.5] - 2026-11-07

- Highlight the full sidebar search field on focus.

## [2.2.4] - 2026-11-07

- Match Phone Access buttons to the rest of the interface.

## [2.2.3] - 2026-11-07

- Show immediate connection progress, clearer access states and setup errors.

## [2.2.2] - 2026-11-07

- Improve remote-session recovery, prevent verification pages from entering reader caches and keep desktop reading available when access settings are unreadable.

## [2.2.1] - 2026-11-07

- Improve Remote Access stability.

## [2.2.0] - 2026-11-07

- Introduce email-protected Cloudflare Remote Access. This feature is removed in v2.2.50.

## [2.1.2] - 2026-11-07

- Improve browser startup diagnostics, reader preferences and font handling.

## [2.1.1] - 2026-11-06

- Clean up obsolete account and hosting features.

## [2.1.0] - 2026-11-06

- Replace OmniReader accounts with one local library profile while preserving legacy data.

## [2.0.0] - 2026-11-06

- Add optional local-network and protected phone access.
- Keep only the two newest Windows packages.

## [1.9.0] - 2026-11-06

- Improve mobile reading and AniList synchronisation.

## [1.8.0] - 2026-11-06

- Add phone LAN access, compact source controls and synced reader preferences.

## [1.7.0] - 2026-11-05

- Unify novel sources and improve LNReader compatibility.

## [1.6.0] - 2026-11-05

- Add continuous reading and default novel sources.

## [1.5.1] - 2026-11-05

- Repair novel sources and simplify source controls.

## [1.5.0] - 2026-11-05

- Add LNReader novel plugins, ordered series and automatic repository updates.
- Scope novel chapter identities to their books.

## [1.4.1] - 2026-11-05

- Open catalogue titles directly and group chapter uploads by scanlator.

## [1.4.0] - 2026-11-05

- Add guest browsing, catalogue discovery and improved tracker matching.

## [1.3.0] - 2026-11-05

- Show readable Comix chapters while the rest of the catalogue loads.

## [1.2.9] - 2026-11-04

- Add novel reading sources, UI scaling, search history and grouped editions.

## [1.2.8] - 2026-11-04

- Fix comic browser callbacks, slow catalogue loading and chapter recovery.

## [1.2.7] - 2026-10-29

- Use native cached comic reads, combined refresh and versioned Windows folders.

## [1.2.6] - 2026-10-29

- Separate source categories and open comic titles progressively.

## [1.2.5] - 2026-10-29

- Simplify Windows startup and tidy the downloadable application layout.

## [1.2.4] - 2026-10-28

- Repair Comix callbacks, touch input and offscreen hosting.

## [1.2.3] - 2026-10-28

- Fix the bundled comic engine/JRE layout.

## [1.2.2] - 2026-10-28

- Improve source cards and recovery from comic-engine startup failures.

## [1.2.1] - 2026-10-28

- Prepare Comix and MangaDot automatically.

## [1.2.0] - 2026-10-28

- Add installable Keiyoushi comic extensions through a private Suwayomi engine.

## [1.1.1] - 2026-10-28

- Improve MyAnimeList score reliability and sort chapters with missing volume metadata.

## [1.1.0] - 2026-10-28

- Add public title ratings, English reading links and Windows packaging.

## [1.0.0] - 2026-10-27

- Initial reader implementation with live sources, a private library, comic/text readers and offline synchronisation.
- Add a Windows launcher for local use.

## [0.1.0] - 2026-10-27

- Early reading-platform prototype with library, reader and offline-sync foundations.

