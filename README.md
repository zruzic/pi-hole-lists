Note: this repository is designed to be used together with strong global lists# Croatia Media Ads – Pi‑hole Blocklist

**Croatian top media ad + tracker domains (Minimal+ blocklist)**  
Curated for Pi‑hole, with a focus on Croatian news / media portals.

This list is opinionated and tuned for a **home network in Croatia** – the goal is to:
- aggressively reduce display / video / popup ads and tracking on the biggest Croatian portals
- keep sites generally functional (logins, comments, paywalls where needed)
- complement, not replace, high‑quality global blocklists (Hagezi, OISD, StevenBlack, …)

---

## What this list targets

The list focuses on:

- **Croatian news & media portals**
  - `index.hr`, `jutarnji.hr`, `vecernji.hr`, `24sata.hr`, `net.hr`, `tportal.hr`, `rtl.hr`,
    `telegram.hr`, `n1info.hr`, `dnevnik.hr` (NovaTV)
- **Their first‑party ad / tracking subdomains**
  - e.g. `adserver.index.hr`, `metrics.jutarnji.hr`, `ads.dnevnik.hr`, `adserver.dnevnik.hr`,  
    `bijelojaje-widget.dnevnik.hr`, etc.
- **External ad networks and trackers actually seen on Croatian portals**
  - Google Ads / DoubleClick endpoints
  - mainstream ad networks (Adform / OpenX / Teads / Ezoic / AppNexus / SmartAdServer / PubMatic / Rubicon / …)
  - local/regional engagement & recommendation platforms (ContentExchange, Upscore, html-load, EBX, …)

The idea is to keep this list **small but high‑impact** – every entry here is based on
real traffic from Croatian media sites.

---

## Blocklist URL

You can add this list directly to Pi‑hole (or any compatible DNS sinkhole) as an adlist:
```text
https://raw.githubusercontent.com/zruzic/pi-hole-lists/main/croatia-media-ads.txt
```
---
## Recommended base blocklists

This list is meant to be a regional supplement, not your only protection.

My current base setup looks roughly like this:

Hagezi popup ads – focused on aggressive popups / redirects

```text
https://cdn.jsdelivr.net/gh/hagezi/dns-blocklists@latest/adblock/popupads.txt
```

Hagezi TIF (Threat Intelligence Feeds) – malware / phishing / C2

```text
https://cdn.jsdelivr.net/gh/hagezi/dns-blocklists@latest/adblock/tif.txt
```






