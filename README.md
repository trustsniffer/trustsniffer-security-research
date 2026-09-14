# Trustsniffer Security Research

Open research notes and reference datasets on web intelligence, on-chain wallet risk, sanctions
research and multi-signal risk methodology.

**Published site:** https://trustsniffer.github.io/trustsniffer-security-research/

## Scope

This repository holds the source of a static research site. It is methodology writing, not product
documentation: what each class of risk signal can support, where it breaks, what the common false
positives look like, and how a finding should be written so that someone can disagree with it on the
evidence.

The datasets are reference material published in the same spirit — narrow, dated, and explicit about
what each row does and does not assert.

## Contents

```
index.html                                     Research hub
research/website-risk-intelligence.html        Domain identity, infrastructure, HTTPS limits, reputation feeds
research/on-chain-wallet-risk.html             Direct vs indirect exposure, fund flows, association vs proof
research/sanctions-screening-research.html     Entity resolution, name collisions, jurisdiction, verification
research/multi-signal-risk-analysis.html       Signal independence, corroboration, weighting pitfalls
data/stablecoin-sanctioned-wallets.html        Dataset documentation
data/sanctioned-wallets-ethereum.csv|.jsonl    Frozen USDT/USDC addresses on Ethereum
data/sanctioned-wallets-tron.csv|.jsonl        Frozen USDT addresses on Tron
data/dataset-manifest.json                     Counts, schema and caveats
assets/css/research.css                        Single stylesheet
robots.txt, sitemap.xml                        Crawl surface
```

## Datasets

`data/` contains addresses whose most recent recorded state on the USDT or USDC token contract is
**frozen**, on Ethereum and Tron. Two facts are kept in separate columns and never merged:

| `designation` | Meaning |
|---|---|
| `sanctions_listed` | The record carries a government designation or seizure-order attribution (OFAC, NBCTF, national seizure orders). |
| `issuer_freeze` | The token issuer blacklisted the address at the contract level. Not by itself a government sanction. |

The build takes the latest event per address and keeps only those still frozen, so addresses that
have been released are not republished. Malformed address strings are excluded rather than repaired.

These files are a point-in-time snapshot, not a live feed, and not a substitute for the publishing
authority's own list or for the token contract's current state. A frozen address does not establish
that its owner committed an offence.

Licence: CC BY 4.0.

## Structure and build

Plain semantic HTML5 with one hand-written stylesheet. No framework, no build step, no JavaScript, no
analytics, no cookies. Each page carries its own `<title>`, meta description, self-referencing
canonical, Open Graph tags and JSON-LD (`TechArticle` for the research notes, `Dataset` for the data
page, `WebSite`/`Organization` on the home page).

## Deployment

GitHub Pages, served from the `main` branch root (`.nojekyll` is present so paths are published
verbatim). Pushing to `main` publishes.

## Related

Trustsniffer's public analysis tools are at https://trustsniffer.com/ — the research here describes
the reasoning those tools implement.
