# Security Policy

## Reporting Vulnerabilities

If you discover a security vulnerability in OsiNet, please report it responsibly.

**DO NOT** open a public GitHub issue for security vulnerabilities.

Instead, contact us directly:

- **Telegram:** [@savaskarofficial](https://t.me/savaskarofficial)
- **Website:** [undercoveritfirm.com](https://undercoveritfirm.com)

We will acknowledge receipt within 48 hours and provide a timeline for a fix.

## Scope

The following are in scope for security reports:

- Vulnerabilities in the OsiNet APK that could compromise user data
- SQLCipher encryption bypass or key extraction
- Network traffic leaks (cleartext where encrypted is expected)
- Proxy/Tor bypass where traffic escapes the configured proxy
- Permission escalation

## Out of Scope

- Vulnerabilities in third-party APIs that OsiNet queries (report those to the API provider)
- Social engineering attacks
- Physical device access attacks
- Root/Magisk-based attacks (rooted devices are inherently compromised)

## Security Architecture

- **Encryption:** SQLCipher AES-256 for all local investigation data
- **Proxy:** SOCKS5/HTTP proxy support with Orbot/Tor integration
- **Network:** All HTTP traffic uses OkHttp with certificate pinning where applicable
- **Telemetry:** Zero — no analytics, no crash reporting, no phone-home
- **Permissions:** Minimal required set, no background location, no contacts access
