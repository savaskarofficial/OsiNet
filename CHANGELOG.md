# Changelog

Application changes below are grounded in the supplied 1.0.7 project notes. Repository maintenance is listed separately; it does not change the APK version.

## Repository refresh — 2026-10-15

- Replaced the broken root `app-debug.apk` link with versioned GitHub Release links.
- Documented actual APK version 1.0.7/code 8, debug package, size and SHA-256; staged the existing APK outside the repository tree.
- Reconciled 84 active Home entries across category counts 15/22/16/11/20.
- Updated case capture/export behavior, Person Recon notes, discovery limits and runtime version display.
- Removed unsupported guarantees about false positives, anonymity, complete provider coverage and reverse-image protection.
- Corrected privacy and permission explanations, and removed unsupported certificate-pinning/all-path proxy claims.
- Retained supplied screenshots and labeled them as earlier device captures.
- Added release notes, release metadata, safe clone/push/release instructions and a minimal-repository publishing route.
- Strengthened binary/source/signing-key ignore rules and updated issue-report guidance.
- Preserved LICENSE, funding, contacts and historical changelog. Excluded the uploaded `.git` directory from this delivery; existing remote history is retained by cloning before applying files.

## APK 1.0.7 — supplied build, 2026-10-11

### Case reports

- Shared readable renderer for snapshot HTML, full HTML and `report.html` within case ZIPs.
- Dark theme, statistics, navigation, result cards, structured tables, notes and print styling.
- Raw payloads remain in collapsed sections with SHA-256 integrity values.
- Full reports read case-linked records transactionally, including retained investigation data; ZIP preserves attachment and JSONL/integrity exports.
- Escaped imported text, constrained HTTP(S) links and a restrictive report content security policy.

### Recorded validation

- 75 JVM tests passed; debug build/lint succeeded with zero lint errors, 39 warnings and 6 informational findings.
- Synthetic report previews reviewed at desktop/mobile widths and in print mode.
- Package/version from APK metadata: `com.undercoveritfirm.osinet.debug`, 1.0.7/code 8.
- These are prior build-verification results, not tests rerun during this documentation refresh.

## Earlier included maintenance — through 1.0.6

- Live Ping output, partial-result retention and traceroute enrichment as hops arrive.
- Traceroute export through Android’s save picker.
- Shared bounded subdomain discovery, passive-name retention and explicit inconclusive/wildcard/source status.
- Person Recon source/query/observation notes, linked to the selected case; persistent drafts across recreation.
- Safer dork domain/keyword rendering and revised operator guidance.
- DNS comparison displays completed results and failure reasons.
- Installed-version metadata in About/Settings.
- Workbench/Web Research removed from navigation while preserving historical data.
- Clearer registration/Reverse WHOIS coverage and shared-host CVE attribution.

## Historical repository versions

The uploaded Git history already contains `v1.1.0`, while its README still advertised 1.0.0. The available APK is actually 1.0.7. No new 1.1.1 APK is fabricated and no existing tag is moved. Publish this build as `apk-v1.0.7` (testing/prerelease). For the original entries, see [archived changelog](docs/legacy-CHANGELOG.md).
