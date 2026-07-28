# Are You Invested in Immigration Enforcement?

**Version 1.7** — July 2026

A public-interest tool that lets anyone search a mutual fund or ETF by ticker symbol to see whether their retirement savings hold stakes in companies profiting from U.S. immigration detention, surveillance, and deportation.

Built by investigative journalist **Jon Nealon** / [`<verify>`](https://jonnealon.github.io)

---

## What It Does

Enter any fund ticker — including the most widely held funds in America — and the tool returns an immediate verdict: **exposed** or **not exposed**, broken down company by company.

Seven publicly traded companies hold active contracts or data agreements with ICE and DHS for detention, surveillance, and deportation:

| Ticker | Company | Role |
|--------|---------|------|
| **GEO** | GEO Group | Largest private detention operator (~42% of ICE beds); runs electronic ankle monitoring via BI Inc. |
| **CXW** | CoreCivic | Second-largest private detention operator; 5 facilities reactivated in 2025 under new ICE contracts |
| **PLTR** | Palantir | Built ImmigrationOS, ELITE raid-targeting platform, and FALCON case management for ICE |
| **AXON** | Axon Enterprise | Sole supplier of tasers and body cameras to ICE; $220M sole-source contract in process |
| **TRI** | Thomson Reuters | CLEAR database provides ICE with license plate data, address history, and criminal records |
| **RELX** | RELX / LexisNexis | Accurint database described by ICE as "mission critical" to enforcement operations |
| **JET** | GlobalX Airlines | Dominant ICE charter airline; flew 80%+ of removal flights in 2024 |

Most investors hold at least one of these without knowing it. Since Palantir joined the S&P 500 in September 2024 and the Nasdaq-100 in December 2024, every standard index fund now holds a stake in the company that built ICE's AI targeting system.

---

## How to Use

Open [`iic_fund_checker.html`](./iic_fund_checker.html) in any browser, or visit the live version at:

**[jonnealon.github.io/StockTool/iic_fund_checker.html](https://jonnealon.github.io/StockTool/iic_fund_checker.html)**

- Type a fund ticker (e.g. `VOO`, `QQQ`, `VTSAX`) and press **Look up**
- Enter multiple tickers separated by commas (e.g. `VOO, IWM, FSKAX`) for a side-by-side comparison
- Hover over any of the seven company cards to see detailed stats including CEO, market cap, revenue, and ICE contract value
- Use the **↓ Show dollar exposure** toggle to calculate your approximate dollar stake

The tool includes a hardcoded database of **over 100 commonly held funds** for instant results with no API call. For any fund not in the database, an AI-powered lookup provides a real-time analysis.

---

## Fund Database

The 100+ hardcoded funds cover:

- **S&P 500:** SPY, VOO, IVV, SPLG, FXAIX, SWPPX, VFIAX, VINIX, FNILX
- **Nasdaq-100:** QQQ, QQQM
- **Total Market (US):** VTI, VTSAX, VTSMX, FSKAX, FZROX, ITOT, SCHB, SWTSX, VITSX
- **Large-Cap Growth:** VUG, SCHG, IWF, IWB, MGK, VGT, XLK
- **Large-Cap Value / Dividend:** VTV, IVE, VIG, SCHD, VYM
- **Mid-Cap:** VO, IJH, MDY
- **Extended Market:** VXF
- **Small-Cap Blend:** IWM, VTWO, VB, SCHA, VSMAX
- **Small-Cap Value:** IJR, IJS, VIOV, VBR, IWN, AVUV, SLYV, DFSV
- **Broad US Composite:** SPTM, DFAC
- **Balanced / Active:** VBIAX, VWELX, FCNTX, ARKK
- **Target Date (Vanguard):** VTXVX, VTHRX, VFORX, VFFVX, VTTSX
- **Target Date (Fidelity):** FDEWX, FFFDX, FFFLX, FFIFX, FIKFX
- **Total World / All-Country:** VT, ACWI
- **International Developed:** VEA, VXUS, EFA, SPDW
- **Emerging Markets:** VWO
- **Bond / Fixed Income:** AGG, BND
- **Commodity:** GLD
- **ESG:** ESGV, ESGU, SUSA

---

## How the Rankings Work

Each fund receives an exposure score based on which companies it holds and how central ICE revenue is to each company's business. The scoring uses a revenue-intensity factor:

- **Score 5:** GEO Group, GlobalX Airlines (ICE contracts are the majority of their business)
- **Score 4:** CoreCivic (~30% of revenue from ICE)
- **Score 2:** Palantir, Axon Enterprise (significant and growing ICE-specific contracts)
- **Score 1:** Thomson Reuters, RELX (ICE contracts are a small fraction of diversified revenue)

Each company's intensity score is multiplied by its approximate index weight in the fund. A small-cap value fund holding GEO and CoreCivic at elevated weights can rank above a total market fund — which is the correct editorial result: concentration in the most ICE-dependent businesses matters more than breadth.

---

## Technical Notes

**Architecture:**
- Single-file HTML/CSS/JavaScript — no framework, no build step
- Over 100 funds hardcoded in the client-side database for instant lookups
- Unknown tickers fall back to a Claude API call via a Vercel serverless proxy
- AI fallback results are cached in session memory

**No external API calls.** The tool runs entirely client-side. If a ticker isn't in the database, the tool returns a "not found" message listing the seven companies to check manually — a more honest result than an uncertain AI guess.

**To run locally:**
Download `iic_fund_checker.html` and open it in any browser. No server, no API key, no dependencies.

**To deploy:**
Upload `iic_fund_checker.html` to any static hosting service — GitHub Pages, Netlify, or a simple web server. No backend required.

---

## Data Sources & Methodology

**Holdings data** is based on known index composition as of July 2026. GEO and CoreCivic index membership was confirmed following the June 27, 2026 Russell US Indexes reconstitution. Palantir and Axon confirmed in S&P 500 and Nasdaq-100. Fund weights are approximate and based on publicly available index data. Holdings change quarterly.

**Company data** sourced from SEC filings, annual reports, USASpending.gov contract records, Human Rights First ICE Flight Monitor, and publicly available earnings disclosures.

**Key contract sources:**
- GEO Group / CoreCivic: SEC Form 10-K filings, USASpending.gov
- Palantir: ImmigrationOS contract documentation, ICE FOIA releases
- Axon: ICE contract records, congressional testimony
- Thomson Reuters / RELX: DHS contract records, ICE ERO operational documents
- GlobalX: Human Rights First ICE Flight Monitor; ICE charter contract records

This tool is for **informational and journalistic purposes only** — not investment advice.

---

## License

This tool is open source. You are free to use, share, and adapt it for non-commercial journalistic or educational purposes with attribution. Please link back to this repository and credit Jon Nealon / `<verify>`.

For commercial use or republication inquiries: [jnealon@gmail.com](mailto:jnealon@gmail.com)
