# nfc-wifi

Single-file smart Wi‑Fi page for NFC tags that works on both Android and iPhone.

**Live:** https://dosdroid.github.io/nfc-wifi/

## How it works

Write two NDEF records to the tag, in this order:

1. **Wi‑Fi record** (`application/vnd.wfa.wsc`) — Android shows its native join prompt.
2. **URI record** → `https://dosdroid.github.io/nfc-wifi/#s=SSID&p=PASSWORD`, the fallback for iPhone.

Opening the page without parameters shows a generator that builds the URL and estimates the NDEF size (NTAG213 / 215 / 216).

Guest view: SSID, copy‑password button, Wi‑Fi QR code, and on iOS/macOS a generated `.mobileconfig` profile install.

### URL parameters (after `#`)

| Param | Meaning |
|---|---|
| `s` | SSID (required) |
| `p` | Password |
| `t` | `WPA` (default), `WEP`, `nopass` |
| `h` | `1` = hidden network |

Credentials live in the URL fragment, which browsers never send to the server, so they don't appear in any hosting logs.
