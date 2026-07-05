# AdblockLists

A collection of AdBlock Plus / DNS-syntax blocklists for blocking Russian disinformation & propaganda websites, and for blocking ads or entire apps/services (FlashScore, TikTok, YouTube).

Each list is a plain-text file using the standard AdBlock domain-blocking syntax (`||domain^`) and can be added directly as a custom filter list to any AdBlock Plus-compatible ad blocker, or to DNS-level blockers (Pi-hole, AdGuard Home, NextDNS, etc.) that support the same format.

## Lists

| File | Title | Purpose | Entries |
|---|---|---|---|
| [`russian-fake-news.txt`](russian-fake-news.txt) | Russian fake news & propaganda DNS Blocklist | Blocks Russian disinformation, state media, and propaganda websites | 435 |
| [`tiktok.txt`](tiktok.txt) | TikTok DNS Blocklist | Blocks the TikTok service (app domains, CDNs, analytics) | 24 |
| [`youtube.txt`](youtube.txt) | YouTube & YouTube Kids DNS Blocklist | Blocks access to YouTube & YouTube Kids services | 20 |
| [`flashscore.txt`](flashscore.txt) | FlashScore APP DNS Blocklist | Blocks ads served inside the FlashScore application | 7 |

### russian-fake-news.txt

The largest and most actively maintained list in this repo. It targets:

- **State-run media & broadcasters** — RT, Sputnik (plus regional editions: `sputnik.by`, `sputnik.kz`, `sputniknews.cn/us/gr`), TASS, RIA Novosti, Rossiya Segodnya group sites (`ukraina.ru`, `inosmi.ru`, `baltnews.com`), Channel One, NTV, Zvezda, VGTRK/Smotrim, TVC, M24, 5-TV, OTR, RTVI, etc.
- **SVR/Kremlin-linked "think tank" outlets** — sites documented by the US Treasury and EUvsDisinfo as disinformation fronts (Strategic Culture Foundation, Katehon, New Eastern Outlook, Geopolitica, OneWorld, Russia Insider, The Duran, RUBaltic, Ritm Eurasia, Fond Strategicheskoi Kultury).
- **War propaganda & content farms** — Rusvesna, Military Review (topwar.ru), Readovka, Voice of Europe, Warfiles, War on Fakes.
- **Fake regional news networks** — large clusters of look-alike "-news.net"/"-news.ru" and "info*.ru" sites (the InfoRos network) posing as independent local Russian/Ukrainian outlets.
- **Doppelgänger campaign clones** — typosquatted domains impersonating legitimate Western outlets (Spiegel, Süddeutsche Zeitung, Bild, Le Monde, Washington Post, FAZ, Daily Mail, Fox News, etc.), documented by VIGINUM and EU DisinfoLab.
- **Portal Kombat / "Pravda" network** — `news-pravda.com`, whose subdomains redistribute pro-Kremlin content across dozens of countries and languages.

Domains are only added when backed by a credible, named source (EUvsDisinfo, DFRLab, VIGINUM/EU DisinfoLab, US Treasury sanctions, Media Bias/Fact Check, etc.) to avoid over-blocking legitimate sites.

## Usage

Add the raw file URL as a custom filter list, e.g. in an AdBlock Plus-compatible browser extension:

```
https://raw.githubusercontent.com/johnmcclane25/AdblockLists/main/russian-fake-news.txt
```

Swap the filename for any other list in the table above. For DNS-level blockers (Pi-hole, AdGuard Home, NextDNS), add the same raw URL as an adlist/blocklist source — the `||domain^` syntax is understood natively by most of these tools, or can be converted with their built-in AdBlock-format importers.

## File format

Every list follows the same header convention:

```
[Adblock Plus]
! Title: <list name>
! Description: <what it blocks>
! Last modified: <date, UTC>
! Syntax: AdBlock
! Number of entries: <count>
!
||domain-one.com^
||domain-two.net^
```

When editing a list, keep the `Number of entries` and `Last modified` header fields in sync with the actual content.
