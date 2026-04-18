# Changelog

All notable changes to OsiNet will be documented in this file.

## [1.1.0] — 2026-04-19

### 🔧 Critical Fixes — Zero False Positives

- **Username Search / Social Profiler / Person Recon / Digital Footprint** — Completely eliminated false-positive detections. Replaced unreliable `http.head()` HTML scraping with API-first `PlatformValidator` using 22 verified platforms across 3 reliability tiers. Garbage usernames now correctly return 0 results instead of 7+ fake matches.
- **Wayback Machine** — Fixed `limit=50` cap that showed wrong first/last dates and fabricated "Total: 50". Now uses 4 separate CDX queries for accurate first/last snapshots, approximate total (CDX pages × 150K), and 100 most-recent deduped snapshots. Added `matchType=exact` to prevent prefix-match false positives.
- **WHOIS Lookup** — Complete rewrite. Now handles both domains AND IPs. Uses RDAP (RFC 9082) as primary with direct registry URLs (VeriSign, APNIC, ARIN, RIPE auto-routed). TCP port 43 kept as fallback only. Shows structured results — no more raw text dumps or browser redirects.
- **Traceroute** — Fixed RTT showing `* ms` on every intermediate hop. Now measures wall-clock RTT via `System.nanoTime()`. GeoIP resolves live per-hop instead of after trace completes. Whois button restored with in-app IP WHOIS auto-lookup.
- **Breach Check** — Removed broken `breachdirectory.org` API. Replaced with Proton Sentinel breach API.
- **Git Secrets** — Rewritten as dork generator. 40+ secret patterns × 3 backends.
- **Crypto Recon** — TRX lookup switched to TronGrid API.
- **MAC Lookup** — Strict regex validation before processing.

### 🚀 Performance

- **120Hz display support** — Opts in to highest available refresh rate on high-refresh panels.
- **Eliminated 4× full-screen overdraw** — Added `windowBackground` to themes.xml, removed redundant Surface wrapper.
- **Home grid optimized** — Memoized filter, stable keys, `@Immutable` data classes, removed double-clip on 91 cards, disabled overscroll glow.

### ✨ New Features

- **Email Dorks** — 70+ dorks across 10 categories
- **IP WHOIS via RDAP** — Auto-detects IP vs domain. Shows network name, CIDR, registrant, abuse contact from correct RIR (APNIC/ARIN/RIPE).
- **Wayback Year/Month Filter** — FilterChip rows for year and month with live re-fetch.
- **Phone Lookup** — Carrier prefix DB (BD/PK/IN/US/UK) with OSINT deep-links.

## [1.0.0] — 2026-04-17

### Initial Release
85+ OSINT tools across 5 categories — zero paid APIs. Full feature list in README.
