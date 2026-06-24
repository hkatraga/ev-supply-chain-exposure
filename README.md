# EV Supply Chain Exposure: Why the Race to Electrify Cars May Be Decided by a Handful of Countries

**A Power BI analysis of EV adoption, critical mineral supply, and refining concentration.**

[Live interactive report →] (https://app.powerbi.com/view?r=eyJrIjoiYjFjNTAzZDEtYTk4MC00ZjljLTg1NjUtZWYyODk0MjE3OWVjIiwidCI6IjhkMjgxZDFkLTljNGQtNGJmNy1iMTZlLTAzMmQxNWRlOWY2YyIsImMiOjN9)

---

## The question

Global EV adoption is accelerating faster than almost any other consumer technology shift in history. But the batteries that power those vehicles depend on a handful of critical minerals, lithium, cobalt, nickel, and graphite, and on the countries that mine and process them.

This project asks: **as EV demand keeps climbing, how exposed is the transition to the small number of countries that control the materials behind it?**

It's built entirely on public data, no scraping, no proprietary sources, and is intentionally descriptive and diagnostic analytics (what is happening, and why), not predictive modeling.

## The four questions

**1. The Demand Surge** — How fast is EV adoption actually moving, and which countries are leading?
Global EV sales grew **39.7x between 2015 and 2024**. As of 2024, 20 countries have crossed 25% EV sales share, 8 have crossed 50%, and 1 (Norway) has crossed 75%.

**2. Where the Raw Materials Come From** — Which countries dominate mining of the key battery minerals?
Lithium mining is the least concentrated of the minerals studied: the top 3 producing countries account for roughly 77% of global output, spread across Australia, Chile, China, and Argentina.

**3. The Refining Bottleneck** — Where are those materials actually processed into battery-ready form?
This is the project's central finding. **Refining is more concentrated than mining for every mineral studied except nickel.** Lithium mining concentration sits at 77%, but lithium chemical processing concentration jumps to **96%**. The same pattern holds for cobalt, graphite, and rare earth elements used in EV drive motors.

**4. The Exposure Verdict** — Bringing it together.
**5 of the 6 critical minerals analyzed are refined predominantly by a single country, China.** Demand for EVs has grown nearly 40x in a decade while the processing capacity that demand depends on has consolidated into a small number of hubs. This isn't a demand problem or a technology problem, it's a concentration problem, and it suggests the pace of global electrification may ultimately be gated by geopolitics rather than chemistry or consumer appetite.

## Data sources

- **IEA Global EV Data Explorer** (Global EV Outlook 2026 release) — EV sales, stock, and sales share by country, 2010–2025
- **Our World in Data** — country-level production share for nickel and cobalt
- **IEA Critical Minerals Data Explorer** — mining vs. refining supply by country for copper, cobalt, lithium, nickel, graphite, and magnet rare earth elements

All three sources are publicly available and free to access. Full data files are included in this repository.

## Tools and techniques

Built in Power BI Desktop. The model uses a star schema with a shared Date dimension across three independent fact tables. Key techniques applied:

- Power Query: merge, append, custom and conditional columns, unit normalization across inconsistent source formats (raw tonnage converted to percent-of-global-total to make minerals comparable)
- DAX: CALCULATE with explicit filter locking (to prevent page-level slicers from overriding fixed KPI cards), TOPN for dynamic top-N ranking inside measures, DIVIDE for safe ratio calculations
- Visuals: ribbon chart (rank-over-time), clustered column with conditional formatting, line charts with linear interpolation, KPI cards with supporting narrative text

## Limitations

This is descriptive and diagnostic analysis, not a forecast. Where the underlying data includes IEA projections (EV Outlook 2035, mineral supply outlooks to 2040), those figures are explicitly excluded from the historical analysis and would need separate, clearly-labeled treatment if extended.

"Top 3 concentration" is a simple, transparent metric chosen deliberately over more complex indices (like HHI) for interpretability. Country-level data necessarily smooths over company-level detail, two countries with similar national shares can have very different competitive dynamics underneath.

## Files in this repository

- `EV_Supply_Chain_Exposure.pbix` — the full Power BI report
- `CriticalMinerals_CountryLevel.csv`, `CriticalMinerals_Top3Share.csv` — cleaned IEA critical minerals data
- `/screenshots` — exported images of all four report pages
- `/raw-data` — source files as downloaded, for full reproducibility

## About

Built as a personal project to apply and extend Power BI / data analysis skills (alongside PL-300 exam preparation) to a subject I'm genuinely interested in, the global shift to electric vehicles and the geopolitics underneath it.

