# SecretDNS

**A free Windows tool that bypasses internet eavesdropping (DPI) with DNS over HTTPS and SNI fragmentation — turned on with a single click.**

English · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [Español](README.es.md) · [Português (Brasil)](README.pt-BR.md) · [Français](README.fr.md)

> This document is a translation. If anything differs, the [Korean version](README.ko.md) is authoritative.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=en)

![SecretDNS screen](images/secretdns-en.png)

## Overview

When you open a website, your computer sends two things in plain text: a **DNS query** asking for the site's IP address, and the **site name (SNI)** carried in the first packet of every HTTPS connection. Inspection equipment (DPI) run by ISPs or network administrators reads both to see which site you are visiting, and can cut the connection or redirect you to a warning page.

SecretDNS closes both holes with one press of the **lock button**.

- **DNS** — Handles your computer's DNS queries over **encrypted DNS (DoH)** with a server such as Cloudflare. Windows network settings are never touched, so the moment you stop the program everything is back to normal — and if the computer shuts down unexpectedly while running, the internet works as usual after a reboot, with nothing left behind.
- **SNI** — **Keeps the site name from being exposed to inspection equipment** during HTTPS connections. The connection itself works as usual, and because only the name part is handled there is almost no slowdown.

Sites that break when fragmented (banks, payment gateways) pass through untouched thanks to a built‑in **exception list**, and the **Report** shows how each site was handled. For sites that DNS bypass cannot open — such as the **451 error** common in countries without internet freedom, where the site itself refuses connections from that country — **Mixed Proxy** routes just those sites through another country. Only the domains you specify go that way, so the rest of your internet keeps its full speed.

SecretDNS is not a VPN. It does not hide your IP address or encrypt all traffic — it handles only the two places used for eavesdropping: DNS and SNI.

## Features

- **One click** — Just press the **lock button** on the home screen. Clicking the tray icon or the lock at the top right of Config toggles it too.
- **DNS over HTTPS** — Cloudflare by default. Add your own servers and check several; SecretDNS switches between them automatically. A **Servers** mode uses a plain DNS server (e.g. 1.1.1.1) without encryption.
- **No Windows settings changed** — The adapter's DNS settings are never edited. Nothing is left behind when you stop, and after a power cut or forced shutdown a reboot brings everything back to normal.
- **SNI fragmentation** — Keeps the site name from being exposed in HTTPS and HTTP connections.
- **Exception / Manual lists** — Choose which sites not to fragment, or only which sites to fragment. Some 160 domains (banks, payments, portals, games …) are built in as exceptions.
- **Browsers only** — Apply fragmentation only to major browsers, leaving games and business software alone. On from the start.
- **Fake packet** — An additional bypass method for networks where fragmentation alone is not enough.
- **Connection that doesn't drop** — Checks that the DNS server is reachable before starting; if the server stops answering while running, the internet stays up and encryption resumes automatically once the server is back. The internet keeps working after sleep or Wi‑Fi changes.
- **Report** — A table of domains and what was applied (encrypted, fragmented, plaintext, via server …), separately for DNS and SNI, in its own window, with copy to clipboard.
- **Mixed Proxy** — Only the domains you list go through an overseas server. Use it for sites blocked with a 451 error that DNS cannot bypass; everything else connects directly as usual, so there is no speed penalty.
- **Auto start · tray** — Run at startup; closing the window sends it to the notification area.
- **22 languages** — Follows the Windows display language, or pick one yourself under **Language** in Config.

## Download / Installation

| Type | Link |
|---|---|
| Installer | [Download](https://down.kilho.net/secretdns?lang=en) |
| Portable (ZIP) | [Download](https://down.kilho.net/secretdns?lang=en&nosetup) |

The installer launches SecretDNS when it finishes and registers **Run at startup**. For the portable version, unzip and run `SecretDNS.exe`. Either way, SecretDNS asks for **administrator rights**.

## Usage

### Getting started

1. Launch SecretDNS. When the administrator prompt appears, click **Yes**.
2. Press the **lock button** in the middle of the home screen. When the lock lights up in gold it is running, and the notification‑area (tray) icon turns gold as well.
3. Use your browser as usual. There is nothing else to do.
4. To turn it off, press the lock again or click the tray icon once. Closing the window (×) doesn't quit — it goes to the tray.

What gets turned on is decided in **Config**, opened with the **gear** button at the top right. Settings are locked while running, so stop first to change them (**Language** and **View log** stay available while running). The lock at the top right of Config runs and stops it directly, so you don't need to go back to the home screen.

### Screen layout

**Home screen** — The **lock button** (Run/Stop) in the middle, the **gear** (Config) at the top right, and the version in the status bar at the bottom. Clicking the logo at the top opens the website (the logo on the other screens does the same).

**Config** — The arrow at the top left returns to the home screen; the lock at the top right runs/stops. The lock is open and gray when stopped, closed and gold while running.

| Item | What it does |
|---|---|
| **DNS Config** — Disabled / Servers / DNS over HTTPS | How DNS queries are handled. **Servers** on the Servers and DNS over HTTPS rows edits that server list |
| **SNI Config** — Disabled / Fragment / Fragmentⓜ | Whether to fragment every site (except the exception list) or only the sites in the manual list |
| **Exception** / **Manual** list | Choosing Fragment shows the exception list right under that row; choosing Fragmentⓜ shows the manual list under its row. One domain per line |
| **Enable Mixed Proxy** | Only listed domains go via an overseas server. When checked, the list box appears right below (requires a DNS setting to be on) |
| **Browsers only** | Apply fragmentation and fake packets to browser traffic only |
| **Enable Fake Packet** | An additional bypass method for networks where fragmentation alone is not enough |
| **Enable Report** + **View log** | Keep a report. **View log** opens the report window |
| **Run at startup** | Start in the tray at logon. If it was running last time, protection is turned on automatically too |
| **Language** | Display language. **System** follows the Windows display language |

**DNS servers** — The list for the side whose **Servers** button you pressed (Servers or DNS over HTTPS) is shown as a table, with **Add** · **Edit** · **Delete** below.

**Report window** — Three columns: **Type** (DNS · SNI · VPN), **Domain**, **Applied**. Each identical line is kept once, and lines with an empty Applied column (sent out untouched) are shown dimmed. **Copy** / **Copy(All)** copy tab‑separated text; **Clear** empties the list. The window is resizable, and when you hide the main window to the tray and open it again, the report window comes back with it.

**Tray icon** — Gray when stopped, gold while running. One click toggles Run/Stop. The right‑click menu has **SecretDNS** (show window) · **Run** · **Stop** · **Kilho.net** · **Quit**. Hovering shows the version and the current state.

### How do I…

**A site redirects to a warning page or the connection drops**
With the default settings (DNS **Servers** or **DNS over HTTPS** + SNI **Fragment**), just pressing the lock solves most cases. Enable Report and visit the site: the `SNI` line should say **Fragment** and the `DNS` line **Plaintext** or **DNS over HTTPS**. If it still doesn't work, try **Enable Fake Packet** below.

**A site stopped working after turning SecretDNS on (bank, payment, game login …)**
That site's traffic doesn't tolerate fragmentation. In Config, add its domain as one line to the **Exception** list under the **Fragment** row and run again.
- Write it **starting with a dot**, like `.example.com`, to match `example.com` and every subdomain (`www.example.com`, `m.example.com`).
- You can paste the URL from the address bar as is — `https://`, `www.` and the trailing path are stripped automatically.
- The list is saved when you click outside the box, leave Config or run, and applies **from the next Run**. Run straight from the lock at the top right of Config — no need to go back to the home screen.
- Some 160 domains — banks, cards, payments, portals, shopping, games, government (`.go.kr`), schools (`.ac.kr`) — are already built in as exceptions, so you don't need to add them. They keep working even if you empty the list.

**Fragment only a few sites and leave everything else alone**
Switch SNI Config to **Fragmentⓜ** and the **Manual** list box appears under that row. Only the domains written here are fragmented; everything else is sent untouched. If only one or two sites give you trouble, this is the safer choice. The rules for writing entries are the same as the exception list, and if the list is empty SecretDNS asks you to enter a domain before running.

**Encrypt DNS only, without fragmentation**
Set DNS Config to **DNS over HTTPS** and SNI Config to **Disabled**. Conversely, to leave DNS alone and use fragmentation only, set DNS to **Disabled**. With both disabled, "There are no features to execute." appears.

**"Cannot connect to the encrypted (DoH) DNS server." appears**
Some office and school networks allow internet access but cannot reach certain DoH servers. Two options:
- Press **Servers** on the DNS over HTTPS row and check a different server in the list (for example **cloudflare-dns.com** from the default list).
- Or switch DNS Config to **Servers**. No encryption, but you still get the effect of using a different DNS server without changing Windows settings.

**Use a different DNS server**
Press **Servers** on the **Servers** or **DNS over HTTPS** row of DNS Config to open that server list.
- **Add** takes a **Name · Address 1 · Address 2** (backup, may be empty). Servers take an IPv4 address such as `8.8.8.8`; DoH takes an address such as `https://1.1.1.1/dns-query` or `https://dns.google/dns-query`.
- Only **checked** entries are used. Check several and SecretDNS moves to another server automatically when one doesn't answer. With none checked, Cloudflare is used.
- The default list has Cloudflare (checked) and Google (unchecked).
- Changes apply **from the next Run**.

**Don't affect games or business software**
Keep **Browsers only** on (it is on from the start). Fragmentation and fake packets are applied only to traffic from major browsers such as Chrome · Edge · Firefox · Whale; other programs are left alone. DNS handling still applies regardless of the program.
If a program other than a browser (a download manager, for example) also needs fragmentation, turn **Browsers only** off.

**Still blocked even with fragmentation**
Try **Enable Fake Packet**. It is an additional bypass method for inspection equipment that fragmentation alone cannot get past, and it does not affect the real connection.

**Open blocked sites by routing only them through an overseas server (Mixed Proxy)**
In countries where internet freedom is not guaranteed, a site may refuse connections coming from that country altogether, and the browser shows a **451 error** (Unavailable For Legal Reasons). This is rarely seen in countries with a free internet. DNS encryption and fragmentation cannot open it — the block is based on the country you connect from. Mixed Proxy sends only those sites through a server in another country.
With a DNS setting on, check **Enable Mixed Proxy** and a list box appears right below. Write one domain per line (`.example.com`, same rule as the exception list) and run.
- Only listed domains go through the overseas server; everything else connects directly as usual. Unlike a full VPN, other sites keep their normal speed.
- A server is assigned automatically each time you run, and if one doesn't answer the next server is used automatically.
- The Report shows type **VPN**, applied **Via server**.
- Mixed Proxy requires a DNS setting to be on and is turned off together when DNS is set to Disabled.

**Have it on every time the computer starts**
Check **Run at startup** (the installer registers this already). At logon it starts in the tray without a window, and **if it was running last time**, protection is turned on automatically. If you stopped it and quit yourself, it waits at the next boot instead.
If Wi‑Fi connects late after boot, SecretDNS starts automatically once the network is up.

**Keep it running after closing the window**
Pressing close (×) sends it to the tray instead of quitting, so there is nothing to set. To quit completely, right‑click the tray icon → **Quit** (a confirmation appears). Quitting turns protection off too.

**Change the display language**
Pick one under **Language** at the bottom of Config and the screen switches right away — even while running. Choose **System** to follow the Windows display language again.

**See how each site is being handled right now**
Turn on **Enable Report** and open the report window with **View log**. Every domain accessed while running is listed one per line. **View log** works while running too.

| Type | Applied | Meaning |
|---|---|---|
| DNS | **DNS over HTTPS** | Looked up via the encrypted server |
| DNS | **Plaintext** | Looked up via the plain server (no encryption) |
| SNI | **Fragment** | The site name was fragmented |
| SNI | (empty) | Sent untouched — the site is on the exception list |
| VPN | **Via server** | Went through the overseas server via Mixed Proxy |

**Copy(All)** pastes into Notepad or Excel with the columns intact.

**Why the internet keeps working even if the DNS server doesn't answer**
SecretDNS checks that the DNS server is reachable before starting, and if the server stops answering for a while during a run, it automatically keeps the internet working. Once the server is back, it returns to normal operation automatically; meanwhile the state is visible in the tray icon and the Report. There is no need to restart it after waking from sleep or switching Wi‑Fi.

**A driver notice appears**
In rare cases a notice may ask you to restart the computer before running. Just restart as instructed.

**The computer shut down while running**
Nothing to worry about. SecretDNS doesn't change Windows network settings and only works while it is running, so after a power cut or forced shutdown the internet is back to normal as soon as you boot. With Run at startup enabled, it starts again by itself after logon.

## Configuration

Changed in **Config** and saved immediately. Most apply **from the next Run**, and settings survive updates.

| Item | Default (installer) | Default (portable) |
|---|---|---|
| DNS Config | Servers | Servers |
| SNI Config | Fragment | Fragment |
| DNS server list | Servers: Cloudflare ✓, Google / DoH: Cloudflare ✓, cloudflare-dns.com ✓, Google | same |
| Enable Mixed Proxy | Off | Off |
| Browsers only | On | On |
| Enable Fake Packet | Off | Off |
| Enable Report | Off | Off |
| Run at startup | On | Off |
| Language | System | System |

The display language follows the Windows display language (22 languages; otherwise English) and can be changed under **Language** in Config.

## Requirements

- Windows 10 or Windows 11 (32‑bit and 64‑bit)
- **Administrator rights** — a permission prompt appears at every launch.
- No additional runtime is required.
- Internet connection — used for the DNS server check and new‑version notices.

## Updates

SecretDNS does **not** update itself. At launch it checks whether a new version exists and shows a notice; pressing **Yes** opens the download page and quits the program. New versions are released manually after internal verification and announced on the [SecretDNS page](https://kilho.net/secretdns). See the [update policy notice](https://en.kilho.net/archives/notice/2940).

## License

SecretDNS is **freeware**. Use it anywhere — at the office, at home, in government offices, at school — free of charge and without restriction, and redistribute it freely.

## Links

- Website: <https://kilho.net/secretdns>
- Forum: <https://kilho.top/forum/qna>
- X (Twitter): <https://www.twitter.com/kilhonet>

© KILHO.NET
