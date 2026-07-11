# nse-screener-data

The full datasets behind **[Twenty-Five Ways We Failed to Beat the Market](https://deshpanda.github.io/nse-screener/)** — every number in that project traces to files in this repository. All from free public sources (NSE, SEC, Internet Archive), collected by the ingest modules in the [main repo](https://github.com/deshpanda/nse-screener), each of which documents the API quirks it works around.

**New to market data? Each section below explains what the dataset IS before what's in it.**

---

### `bhav/` — daily prices & delivery (2016→)
One file per trading day. For every NSE stock: open/high/low/close prices, volume (shares traded), turnover (₹ value), and **delivery** — how many traded shares were actually *kept* overnight vs day-traded. Delivery matters because it separates real accumulation from churn. ~2,700 days × ~2,400 stocks.
*Gotcha: prices are as-published — apply corporate-action adjustment (main repo) before computing returns, or splits will look like crashes.*

### `futstk/` — stock futures (2016→)
Daily data for every stock's futures contracts: price, **open interest** (how many contracts are outstanding — i.e., how much betting money is positioned), and its daily change. The derivatives market's opinion, in numbers.

### `fr_xbrl/` — quarterly results (2018→)
43,000+ company quarterly profit numbers parsed from regulatory XBRL filings, each with the **exact timestamp it became public**. That timestamp is the treasure: it lets a backtest honestly "know" a number only after the market did.

### `pit/` — insider disclosures (2017→)
290,000+ filings: every time a promoter, director, or employee bought/sold their own company's shares — who, how (open-market vs ESOP grant), value, and when disclosed. Includes 29,000+ share-**pledge** creation/revocation events (founders borrowing against their shares).

### `deals_hist/` — named big trades (2016→)
151,000+ bulk/block deals: any single trade above 0.5% of a company, with the **buyer's and seller's names**. The raw material for testing every "follow the smart money" theory.

### `ann_full/` — all corporate announcements (2016→)
1.26M announcements with category labels (results, ratings, resignations, meetings…). `announcements/` is the older buyback/order-win subset with a random control sample.

### `shareholding/` — quarterly ownership (long history)
Per company: promoter % vs public % each quarter, with disclosure timestamps — up to ~90 quarters per symbol. Who owns the company, and how that changes.

### `indices/` — sector index levels (2016→)
Daily closes for 12+ NSE sector indices (Bank, IT, Pharma…). Sector-level benchmarks.

### `index_members/` — index membership snapshots
13 point-in-time Nifty constituent lists recovered from the Internet Archive. Partial by nature; documented honestly.

### `pledge/` — monthly pledge snapshots (2026→)
A dataset being *farmed*: full promoter-pledge state captured monthly, because the exchange only publishes "now."

### `mto/` — delivery data 2016–19
The older archive format that supplied delivery figures before 2020 (already merged into `bhav/` in the main repo's pipeline).

---

**License/intent:** redistributed snapshots of public disclosures, for research reproducibility. Nothing here is investment advice. If you use this, the main repo's Chapter 3 ("the data will lie to you") is required reading — raw data has traps.
