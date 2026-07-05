<div align="center">

#  GhostyEye OSINT

### Advanced Intelligence Platform · 

**Created by [REI](https://github.com/REI) · [ghostyeye.dpdns](https://ghostyeye.dpdns.org)**
https://ghostyeye.dpdns.org

*The most comprehensive free OSINT toolkit — 50+ modules, 100% client-side, zero signup.*

![License](https://img.shields.io/badge/license-MIT-00ff41?style=for-the-badge&labelColor=000300)
![Version](https://img.shields.io/badge/version-2.0.0-00ff41?style=for-the-badge&labelColor=000300)
![Status](https://img.shields.io/badge/status-stable-00ff41?style=for-the-badge&labelColor=000300)
![Pricing](https://img.shields.io/badge/pricing-FREE-00ff41?style=for-the-badge&labelColor=000300)
![PWA](https://img.shields.io/badge/PWA-installable-00ff41?style=for-the-badge&labelColor=000300)

</div>

---

##  What is GhostyEye?

GhostyEye is a **free, open, client-side OSINT (Open Source Intelligence) toolkit** that runs entirely in your browser. No servers, no logs, no tracking — every query is performed directly from your machine using free public APIs.

Investigate emails, usernames, domains, IPs, phone numbers, and crypto wallets with **50+ intelligence modules** running in parallel. Watch results stream live to a hacker-style terminal dashboard, then export your findings in 10 different formats — including STIX, MISP, and JSON-LD for SIEM ingestion.

> ⚠️ **For authorized security research, fraud prevention, and identity verification only.** You are solely responsible for compliance with applicable laws.

---

##  Key Features

###  Deep Investigation (9 modules)
| Module | Description |
|--------|-------------|
| **Email Validation** | Format, disposable, MX, alias checks (Disify, Kickbox, Mailcheck) |
| **Gravatar Profile** | Detect profile picture & public profile |
| **GitHub Account Discovery** | Search by email, fetch detailed profile |
| **Have I Been Pwned** | Breach checks across billions of leaked records |
| **Infostealer Log Checks** | GitHub, IntelX, BreachDirectory, LeakCheck, DeHashed |
| **PGP Public Key Lookup** | keys.openpgp.org directory |
| **DNS Records** | A, AAAA, MX, TXT, NS, CAA, SOA (Cloudflare + Google DoH) |
| **100+ Platform Username Search** | Silent detection — no alert to target |
| **Domain & Subdomain Analysis** | Brute-force 100+ common subs + PassiveDNS |

###  AI/ML Enhancements (7 modules)
| Module | Description |
|--------|-------------|
| **AI Profile Synthesis** | LLM-generated digital profile breakdown (Pollinations.AI, free) |
| **Risk Assessment** | Algorithmic 0-100 scoring + LLM-cited reasoning |
| **Network Graph** | D3.js force-directed interactive entity graph |
| **Email Pattern Predictor** | 15 format variations from name + domain |
| **Username Similarity Engine** | 30 typo-squatted variants with Levenshtein scoring |
| **Anomaly Detection** | Flags unusual breach patterns & clustering |
| **Sentiment Analysis** | LLM-powered tone & risk analysis |

###  Visualization & UX (6 modules)
| Module | Description |
|--------|-------------|
| **Live SSE Stream** | Real-time terminal-style intel feed with timestamps |
| **Breach Timeline** | Interactive Chart.js timeline with severity coloring |
| **Geographic Map** | Dark-theme Leaflet map with IP/domain markers |
| **Activity Heatmap** | 7×24 grid showing activity patterns |
| **Command Palette** | Ctrl+K, 50 commands, fuzzy search, keyboard nav |
| **Investigation Comparison** | Side-by-side target comparison with overlap detection |

###  Monitoring & Automation (5 modules)
| Module | Description |
|--------|-------------|
| **Bulk CSV Investigation** | Process 200 targets at once, export merged CSV |
| **Continuous Monitoring** | Schedule recurring scans (hourly/daily/weekly) |
| **Diff Engine** | Track changes over time, alert on new breaches |
| **Webhook Notifications** | POST to Slack/Discord on scan completion |
| **Scheduled Scans** | Cron-style scheduling with localStorage persistence |

###  Privacy & Security (5 modules)
| Module | Description |
|--------|-------------|
| **Encrypted Vault** | AES-GCM 256-bit via Web Crypto API |
| **Self-Destruct History** | Auto-wipe after 1h/6h/24h/7d (Paranoia Mode) |
| **Audit Log** | Tracks every query/action (200 entries) |
| **Request Obfuscation** | Randomize user-agents toggle |
| **Tor Routing** | Documentation + 3 deployment strategies |

###  Export & Integration (10 formats)
| Format | Use Case |
|--------|----------|
| **JSON** | Full structured data dump |
| **CSV** | Spreadsheet analysis |
| **PDF Report** | LLM-written investigation brief (green-on-black theme) |
| **Markdown** | Clean `.md` for GitHub/Notion |
| **STIX/TAXII** | Industry-standard threat intel for SOC/SIEM |
| **JSON-LD** | Semantic web linked data |
| **MISP Feed** | MISP event format with attributes |
| **Shareable Link** | Encrypted URL with base64 results |
| **Print** | Native print-to-PDF |
| **Clear** | Reset current investigation |

###  Specialized Verticals (5 modules)
| Vertical | Description |
|----------|-------------|
| **Corporate Intelligence** | Domain → employees → infrastructure mapping |
| **Crypto Investigation** | Wallet → transactions → exchange flows |
| **Brand Protection** | Typosquat generation + social impersonation check |
| **Threat Actor Profiling** | LLM-generated actor profile with TTPs |
| **Romance Scam Detection** | 7 scam database cross-references |

---

##  Quick Start

### Option 1: Download & Run Locally
```bash
# Download and extract the ZIP
unzip ghostyeye-osint.zip
cd osint-tool

# Open in browser (any modern browser works)
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 2: Use the Live Instance
Visit **[ghostyeye.dpdns](https://ghostyeye.dpdns.org)** — no installation required.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+K` / `Cmd+K` | Open Command Palette |
| `↑` / `↓` | Navigate palette commands |
| `Enter` | Execute selected command |
| `Esc` | Close modal / palette |
| `Tab` | Navigate between elements |

---

##  Developer REST API

GhostyEye exposes a free, no-auth REST API via URL parameters:

### Endpoints

```http
GET /?action=email&email=user@example.com
GET /?action=username&u=johndoe
GET /?action=domain&d=example.com
GET /?action=ip&ip=8.8.8.8
```

### JavaScript Example

```javascript
// Run an email investigation from your code
async function lookupEmail(email) {
  const url = `https://ghostyeye.dpdns.org/?action=email&email=${email}`;
  const res = await fetch(url);
  const json = await res.json();
  return json;
}

// Response includes:
// - validation, gravatar, github, breaches
// - infostealer, pgp, dns, usernames
// - risk (algorithmic score + LLM reasoning)
// - aiSynthesis (LLM profile breakdown)
const result = await lookupEmail("test@example.com");
console.log(result.risk.score);      // 0-100
console.log(result.aiSynthesis);     // LLM text
```

### cURL Example

```bash
curl -L "https://ghostyeye.dpdns.org/?action=email&email=test@example.com" \
  -o "report.json"
```

> No API key, no rate limits, no authentication. Self-host GhostyEye to any static host and you have your own free OSINT API endpoint.

---

## 🔌 APIs Used (All Free)

GhostyEye is powered by these free public APIs. All requests are made directly from the browser.

| API | Purpose |
|-----|---------|
| [Cloudflare DNS over HTTPS](https://developers.cloudflare.com/1.1.1.1/encryption/dns-over-https/) | DNS records (A, AAAA, MX, TXT, NS, CAA, SOA) |
| [Google DNS over HTTPS](https://developers.google.com/speed/public-dns/docs/doh) | DNS fallback resolver |
| [Disify](https://www.disify.com/) | Email format, disposable & alias check |
| [Kickbox Open API](https://open.kickbox.com/) | Disposable email detection |
| [Mailcheck.ai](https://www.mailcheck.ai/) | Domain validity & risk |
| [Gravatar](https://gravatar.com/) | Globally recognized avatar profile |
| [GitHub API](https://docs.github.com/rest) | Search users by public email |
| [Have I Been Pwned](https://haveibeenpwned.com/) | Data breach & password check |
| [keys.openpgp.org](https://keys.openpgp.org/) | PGP public key directory |
| [Unavatar.io](https://unavatar.io/) | Cross-platform avatar resolver |
| [Intelligence X](https://intelx.io/) | Infostealer log search |
| [BreachDirectory](https://breachdirectory.org/) | Free breach database |
| [LeakCheck](https://leakcheck.io/) | Leaked credential search |
| [DeHashed](https://dehashed.com/) | Breached data search engine |
| [Pollinations.AI](https://pollinations.ai/) | Free LLM for AI synthesis |
| [crt.sh](https://crt.sh/) | SSL certificate transparency logs |
| [Wayback Machine](https://web.archive.org/) | Archived web content |
| [RDAP.org](https://rdap.org/) | Domain registration data |
| [blockchain.info](https://blockchain.info/) | Bitcoin wallet lookup |
| [Ethplorer](https://ethplorer.io/) | Ethereum wallet lookup |
| [ipapi.co](https://ipapi.co/) | IP geolocation |
| [ipinfo.io](https://ipinfo.io/) | IP info (ISP, ASN, hostname) |
| [DuckDuckGo Icons](https://duckduckgo.com/) | Favicon service |

---

## 📁 Project Structure

```
ghostyeye-osint/
├── index.html          # Entry point (24 KB)
├── styles.css          # Hacker terminal design system (62 KB)
├── app.js              # Core OSINT engine (136 KB)
├── advanced.js         # 42 advanced feature modules (148 KB)
├── sw.js               # Service worker (PWA offline)
├── manifest.json       # PWA configuration
└── icons/              # SVG + PNG icons (7 variants)
    ├── icon.svg
    ├── icon-16.png
    ├── icon-32.png
    ├── icon-180.png
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-maskable.svg
    └── icon-maskable-512.png
```

**Total size:** 184 KB (gzipped ~50 KB) — no build step, no dependencies.

---

##  Design Philosophy

GhostyEye uses a **hacker terminal aesthetic** inspired by Matrix CRT monitors:

- **Pure black** background (`#000300`) with **neon Matrix green** (`#00ff41`) text
- **CRT scanlines** overlay for authentic retro feel
- **Subtle flicker** animation
- **Vignette** darkened corners
- **Animated grid** background with radar-shift
- **Monospace typography** (JetBrains Mono + Share Tech Mono)
- **ASCII corner brackets** on every panel (`⌐` `¬`)
- **Neon glow** on all interactive elements
- **Terminal-style prefixes** (`>`, `//`, `##`, `[!]`)
- **Dashed/dotted borders** instead of solid

All text has a subtle text-shadow glow for that authentic phosphor-screen look.

---

##  Configuration

### Optional API Keys (all free)

Add these in **Settings** (gear icon in header) for enhanced results:

| Key | Source | Purpose |
|-----|--------|---------|
| HIBP API Key | [haveibeenpwned.com/API/Key](https://haveibeenpwned.com/API/Key) | In-app breach results (otherwise links to HIBP) |
| Hunter.io API Key | [hunter.io](https://hunter.io/) | Email finder enrichment (free tier: 25/mo) |

All other features work without any API keys.

### Toggleable Modules

In Settings, you can enable/disable individual scan modules:
- Gravatar Profile Lookup
- GitHub Account Search
- Data Breach Check (HIBP)
- Cross-Platform Username Search
- PGP Key Lookup
- DNS Records Lookup

---

##  Screenshots

<div align="center">

| Landing Page | Email Investigation | Network Graph |
|:---:|:---:|:---:|
| ![Landing](https://via.placeholder.com/400x250/000300/00ff41?text=Landing+Page) | ![Email](https://via.placeholder.com/400x250/000300/00ff41?text=Email+Scan) | ![Graph](https://via.placeholder.com/400x250/000300/00ff41?text=D3+Graph) |

| Command Palette | Bulk CSV | Live Stream |
|:---:|:---:|:---:|
| ![Palette](https://via.placeholder.com/400x250/000300/00ff41?text=Ctrl%2BK+Palette) | ![Bulk](https://via.placeholder.com/400x250/000300/00ff41?text=Bulk+CSV) | ![Stream](https://via.placeholder.com/400x250/000300/00ff41?text=Live+Stream) |

</div>

---

##  Contributing

Contributions are welcome! This is a static project — no build step required.

### Development Setup
```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/ghostyeye.git
cd ghostyeye

# Serve locally (any static server works)
python3 -m http.server 8000
# Open http://localhost:8000
```

### Guidelines
1. Keep it **100% client-side** — no backend, no server-side code
2. Keep it **100% free** — no paid APIs, no API keys required for core features
3. Maintain the **hacker terminal aesthetic** — green-on-black, monospace, glow
4. Test in **all modern browsers** (Chrome, Firefox, Safari, Edge)
5. Ensure **zero JavaScript errors** in console
6. Update the **service worker cache version** when files change

### Pull Request Process
1. Fork the repo
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

##  Stats

- **50+** investigation modules
- **100+** platforms searched
- **18+** free APIs integrated
- **10** export formats
- **0** servers required
- **0** API keys required (HIBP optional)
- **0** tracking / analytics
- **184 KB** total size
- **100%** free, forever

---

##  Changelog

### v1.0.9 (2026-07-05)
-  **GhostyEye** (created by REI)
-  Added 42 advanced features (SSL, Wayback, Dorking, Crypto, Network Graph, Bulk CSV, Vault, STIX/MISP export, etc.)
-  Hacker terminal aesthetic (CRT scanlines, neon glow, ASCII brackets)
-  Command Palette (Ctrl+K) with 50 commands
-  AI Profile Synthesis via Pollinations.AI
-  Algorithmic Risk Scoring with LLM reasoning
-  PWA with offline support
-  Replaced all `prompt()` calls with custom modal inputs
-  Fixed CSS class typo (`text-daint` → `text-dim`)
-  Fixed command palette async action race condition
-  Updated service worker cache to include `advanced.js`

### v1.0.8 (2026-07-04)
-  Initial release
-  Email, username, domain, phone, IP investigation modes
-  Live stream panel
-  11 result cards per email investigation
-  39 platform username search
-  Glassmorphism → Hacker terminal redesign

---

##  Legal & Ethical Use

GhostyEye is provided for **authorized security research, fraud prevention, and identity verification only**.

###  Allowed Use Cases
- Security research and penetration testing (with authorization)
- Fraud prevention and identity verification
- Threat intelligence gathering
- Brand protection and impersonation detection
- Academic research and education
- Personal digital footprint assessment

###  Prohibited Use Cases
- Stalking or harassment
- Doxxing or revealing private information
- Identity theft
- Any unlawful activity
- Any activity that violates applicable laws

**You are solely responsible for compliance with all applicable laws in your jurisdiction.** The creators and contributors of GhostyEye are not liable for any misuse of this tool.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) file for details.

You are free to:
-  Private use

---

##  Author

<div align="center">

**REI**

 [ghostyeye.dpdns](https://ghostyeye.dpdns.org)

Built for the OSINT community with ♥ and zero tracking.

</div>

---

##  Star History

If GhostyEye helped you, please consider starring the repo — it helps others discover the tool.

<div align="center">

[![Star History Chart](https://api.star-history.com/svg?repos=777rei/GhostyEye&type=Date)](https://star-history.com/#YOUR_USERNAME/ghostyeye&Date)

</div>

---

<div align="center">

** GhostyEye OSINT  · Created by REI · ghostyeye.dpdns.org **

*Stay curious. Stay ethical. Stay free.*

</div>
