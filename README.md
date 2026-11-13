# Croatia Media Ads – Pi‑hole Blocklist

[![Blocklist](https://img.shields.io/badge/Blocklist-Active-brightgreen.svg)](#blocklist-url)
[![Focus](https://img.shields.io/badge/Focus-Croatian%20Media-blue.svg)](#what-this-list-targets)
[![Format](https://img.shields.io/badge/Format-Plain%20Domains-orange.svg)](#blocklist-url)

> [!NOTE]
> This repository is a targeted regional blocklist designed to be used alongside high-quality global blocklists (such as HaGeZi, StevenBlack, and Firebog).

**Croatian top media ad + tracker domains (Minimal+ blocklist)**  
Curated specifically for Pi‑hole, AdGuard Home, and DNS sinkholes with a dedicated focus on Croatian news and media portals.

This list is opinionated and tuned for a **home network in Croatia**:
- **Aggressively blocks** display banners, outstream video ads, wallpaper takeovers, and audience telemetry across major Croatian portals.
- **Maintains functionality**: Preserves user logins, comments, video players, and paywall/subscription flows.
- **Audited against real traffic**: Every domain in this list is actively verified against real network query logs.

---

## What This List Targets

### 1. Major Croatian Portals & Subdomains
- **National Portals**: `index.hr`, `jutarnji.hr`, `vecernji.hr`, `24sata.hr`, `net.hr`, `tportal.hr`, `rtl.hr`, `telegram.hr`, `n1info.hr`, `dnevnik.hr` (NovaTV).
- **Regional & Local Portals**: `slobodnadalmacija.hr`, `novilist.hr`, `glasistre.hr`, `glas-slavonije.hr`, `zagreb.info`, `dalmacijadanas.hr`, `dalmatinskiportal.hr`, etc.
- **First-Party Ad / Tracking Subdomains**: e.g., `adserver.index.hr`, `metrics.jutarnji.hr`, `ads.dnevnik.hr`, `videoads.dnevnik.hr`, `adserver.slobodnadalmacija.hr`.

### 2. Regional Video & Rich-Media Frameworks
- **Outstream Floating Video Ads**: `video.onnetwork.tv`, `cdn.onnetwork.tv`, `cdnt.onnetwork.tv` (used on Jutarnji, Net.hr).
- **Full-Page Wallpaper / Takeover Ads**: `wrappio.dev`, `cdn.wrappio.dev` (used on Večernji, 24sata).
- **Video Pre-roll & Mid-roll**: `videoads.dnevnik.hr` (NovaTV video player ads).

### 3. Domestic Analytics & Audience Measurement
- **DotMetrics Network**: `script.dotmetrics.net` and the newer `dotmetrics.rocks` / `script.dotmetrics.rocks` endpoints.
- **Audience & Telemetry**: `contentexchange.me`, `upscore.com` (`hit-pool.upscore.com`), `cdn.optmn.cloud`, `cme-api.bloomreach.co`, `smartocto.com`.
- **E-Commerce / Retail Tracking**: `metrics.iponcomp.hr`.

### 4. Anti-Adblock & Ad-Reinsertion Proxies
- Blocks dynamic recovery proxies that attempt to reinject ads when standard networks are blocked: `silk.caringyarn.pro`, `btloader.com`, and `*.html-load.com`.

---

## Blocklist URL

Add this URL into your Pi‑hole (**Adlists** / **Lists**) or AdGuard Home:

```text
https://raw.githubusercontent.com/zruzic/pi-hole-lists/main/croatia-media-ads.txt
```

---

## Recommended Base Setup

This regional list is meant to be a supplement. For full network-wide protection, pair it with these tested base blocklists:

#### 1. General & Malware Protection (HaGeZi)
```text
# HaGeZi Multi PRO (Comprehensive ad, tracker & telemetry protection)
https://raw.githubusercontent.com/hagezi/dns-blocklists/main/adblock/pro.txt

# HaGeZi Pop-Up Ads (Aggressive popups, push notifications & redirects)
https://cdn.jsdelivr.net/gh/hagezi/dns-blocklists@latest/adblock/popupads.txt

# HaGeZi TIF (Threat Intelligence Feeds – malware, phishing, C2)
https://cdn.jsdelivr.net/gh/hagezi/dns-blocklists@latest/adblock/tif.txt
```

#### 2. General Clean Lists (StevenBlack & Firebog)
```text
# StevenBlack Unified Hosts
https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts

# Firebog AdGuard DNS List
https://v.firebog.net/hosts/AdguardDNS.txt

# Firebog EasyList & EasyPrivacy
https://v.firebog.net/hosts/Easylist.txt
https://v.firebog.net/hosts/Easyprivacy.txt
```

---

## Best Practices & Tips

### DNS vs. In-Browser Filtering
> [!TIP]
> **DNS blockers (like Pi‑hole)** operate at the domain level. They successfully stop ad servers, tracking beacons, and video ad streams from downloading.  
> However, Croatian portals heavily utilize **first-party native content** (e.g. *Index Oglasi* on `index.hr`, *Hanza Native Studio* on `jutarnji.hr`, and sponsored PR articles) that share the same domain and IP address as the news articles.  
> To remove empty whitespace containers and collapse in-feed sponsored cards, pair your Pi-hole setup with a browser extension like **uBlock Origin** (enabling the built-in *Dandelion Sprout's Serbo-Croatian* filter).

### Prevent Browsers from Bypassing Pi‑hole
- **Chrome / Brave / Edge**: Verify in browser settings that **"Use secure DNS" (DoH)** is set to *Off* (or *"With your current service provider"*), so queries do not bypass Pi-hole over encrypted HTTPS.
- **Apple Devices (Safari)**: Add `mask.icloud.com` and `mask-h2.icloud.com` to your Pi-hole blacklist. This signals Apple devices per official spec to disable iCloud Private Relay on your home network and use Pi-hole instead.
