# Kamsarmax ship finance model

An Excel model of buying a 2016-built 82,000 dwt Kamsarmax bulk carrier in January 2027 on a 3-year time charter, financed with a first-lien senior loan capped at 60% loan-to-value, and selling it after five years. It asks two questions: is the loan safe, and what does the owner earn as charter rates fall?

**Short answer: good loan, thin equity.** Sized on the charter's cash flow, the loan is US$14.4m (42.5% of the price) and is repaid in full in all six scenarios. The owner earns 2.3% a year if rates hold at today's level and loses money in every weaker case.

| Scenario | Hire after charter | Exit value | Equity IRR | Min DSCR | Lowest security cover | Balloon / exit value |
|---|---|---|---|---|---|---|
| 1. Rates hold | US$17,500/day | US$24.5m | 2.3% | 1.33x | 2.47x | 29.5% |
| 2. Mid-cycle | US$15,000/day | US$22.1m | -2.1% | 1.24x | 2.22x | 32.7% |
| 3. Soft market | US$12,500/day | US$19.6m | -7.5% | 0.84x | 1.98x | 36.8% |
| 4. Downturn | US$10,000/day | US$15.9m | -17.1% | 0.42x | 1.61x | 45.3% |
| 5. Downturn + charterer default | US$10,000/day | US$15.9m | -23.9% | 0.25x | 1.61x | 45.3% |
| 6. Rates hold, loan at full 60% LTV | US$17,500/day | US$24.5m | 0.8% | 0.94x | 1.75x | 41.6% |

What the numbers say:

- **The loan.** The 60% cap is not the binding limit; a 1.30x DSCR on contracted charter cash flow is. Year-1 cash breakeven is about US$15,200/day against US$17,500 of hire. The ship's value could fall about 45% before a 130% minimum value clause is hit. Lender IRR is 7.0% (SOFR 3.95% + 2.75% margin + 1% upfront fee).
- **The equity.** At US$34m the owner needs about US$30,200/day after the charter, or a purchase price near US$24.5m, to earn 10%. The ship returns about 4.1% unlevered, below the 6.7% cost of debt, so lending the full 60% (scenario 6) lowers the equity return and pushes DSCR below 1.0x in years 1 and 2.

## How the model works

- **Operations:** charter hire for 3 years, then the scenario's open-market rate; 5% commissions; 5 off-hire days a year plus 20 for an intermediate dry-dock in 2029, funded from a reserve built up in 2027-28; operating costs and G&A rising 3% a year.
- **Loan sizing:** the lower of 60% of the price and the loan whose level debt service the weakest charter year covers 1.30 times. 5-year tenor, 10-year repayment profile, 50% balloon repaid from the sale.
- **Vessel value:** straight-line from the purchase price to scrap value (13,500 LDT at US$480/LDT) over a 25-year life, times a scenario adjustment, floored at scrap. Used for the security cover test each year and the exit price.
- **Returns:** equity, unlevered and lender cash flows and IRRs, minimum DSCR and security cover, balloon as % of exit value, the open-market hire and the purchase price needed for a 10% equity IRR.

Sheets: `Cover` (key results), `Inputs` (every assumption with its source; pick the active scenario), `Model` (full annual cash flows for the active scenario), `Scenarios` (all six, each calculated in full), `Sensitivity` (equity IRR by open-market hire and exit value), `Checks` (16 checks, all passing). 1,772 live formulas; blue cells are inputs.

I checked the workbook against a separate Python version of the same logic: loan, equity IRR, DSCR and security cover match to four decimal places in every scenario tested.

## Main sources

- Compass Maritime Services, Weekly Report, 2 Nov 2026: 10-year-old Kamsarmax US$34m, Panamax 12-month time charter US$18,500/day, recycling prices, orderbook.
- Baltic Exchange weekly report, 30 Oct 2026; Diana Shipping Kamsarmax fixtures at US$16,650 and US$16,850/day (2026).
- Star Bulk Carriers Q1 2026: operating costs US$5,045/day, net G&A US$1,375/day per vessel.
- Costamare Bulkers Form 6-K, Q1 2026: dry bulk loan with quarterly instalments and a balloon.
- Societe Generale, January 2026: margins of 1.00-1.50% over SOFR for top-tier owners.
- BIMCO Dry Bulk Shipping Market Overview and Outlook, October 2026.
- SOFR 3.95% on 2 Nov 2026 (New York Fed data).

Also in this repo: `Kamsarmax_Loan_Teaser.pptx`, a two-page teaser for the loan aimed at institutional debt investors.

Illustrative analysis of a hypothetical vessel. Several inputs are my own assumptions and are marked as such on the Inputs sheet. Not investment advice.
