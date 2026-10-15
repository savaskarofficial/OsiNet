# Security policy

Report vulnerabilities privately through [Telegram](https://t.me/savaskarofficial) or the contact options at [Undercover IT Firm](https://undercoveritfirm.com). Do not post credentials, case evidence or exploitable details in public issues.

Include the exact APK version/package, device and Android version, affected feature, minimal reproduction steps and expected/observed impact. Use synthetic or redacted evidence. Avoid sending private keys or account tokens. Response timing is not guaranteed.

## Scope

- Unauthorized access to local case/history data or SQLCipher key material.
- Unsafe file/report import/export, injection and component exposure.
- Unexpected traffic leakage or a tool violating its configured network behavior.
- Permission/lifecycle failures with security impact.

Report vulnerabilities in external services to their respective operators. Root or physical access changes the threat model but does not make every app bug irrelevant; describe the prerequisites precisely.

## Security boundaries

The local case/history database uses SQLCipher. Exported files and shared text are outside that database’s encryption. Browser/provider queries disclose data to their recipients. Proxy coverage varies by protocol/tool; anonymity, universal certificate pinning and universal HTTPS are not claimed. HTTP inspection permits cleartext traffic. Image transformation is not a guarantee against reverse-image matching.

The distributed 1.0.7 artifact is a debug/testing build, not a production hardening certification. Only that supplied artifact is described here; other releases may differ. This repository contains no application source or signing keys. Keep signing material private and verify release checksums before installing.
