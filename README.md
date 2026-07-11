# nse-screener-data

The full datasets behind https://deshpanda.github.io/nse-screener/ —
every panel the verdicts rest on, as-parsed. Rebuild any of them from
source with the ingest modules in the main repo (each file documents its
source APIs and quirks): https://github.com/deshpanda/nse-screener

| dir | contents |
|---|---|
| bhav/ | daily OHLCV+delivery per stock, 2016→ (split-adjust via main repo) |
| futstk/ | daily stock-futures near+far contracts: OI, close, settle |
| pit/ | insider (PIT) disclosures 2017→ |
| ann_full/ | all corporate announcements, categorized |
| announcements/ | buyback/order-win subset + control sample |
| fr_xbrl/ | parsed quarterly results (broadcast-timestamped) |
| deals_hist/ | bulk/block deals 2016→ |
| mto/ | delivery data 2016-19 (merged into bhav in main repo) |

Not investment advice. Data © respective exchanges; redistributed
snapshots of public disclosures for research reproducibility.
