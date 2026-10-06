# Uber One — Membership Churn & High-Value Member Early Warning

A retention analysis of a subscription membership programme: who churns, how early the signal appears, and which members are worth protecting first. Built in Tableau on a simulated members-and-transactions dataset.

Coursework project for **APAN 5800 Data Storytelling & Visualisation**, Columbia University, Sep–Dec 2025.

---

## The question

Sign-ups were growing, but a large share of members cancelled within three months of the trial ending. The useful question is not *how many* churn — it is **whether churn announces itself before it happens**, and if so, how early.

It does.

## What the data shows

**Churn is a slow fade, not a sudden exit.** Plotting Recency (days since last order) against order Frequency separates the two populations cleanly: churned members cluster in the **high-recency, low-frequency** region, while active members sit at low recency and higher frequency. Members stop *using* the subscription long before they cancel it, which means cancellation is a lagging indicator and recency is a leading one.

**There is a warning zone at 30–50 days.** In that recency band active and churned members overlap. These are people who are drifting but have not left — the only window where intervention is still cheap. Outside it, you are either spending on people who were never going to leave, or chasing people who have already gone.

**Some of the drifting members are the expensive ones.** A subset of high-spend, Eats-first members shows recency past 35 days while still counted as active. They are the highest-value-at-risk segment: small in number, disproportionate in revenue.

**The first→second order is the real conversion.** The largest drop-off happens before the second order — most members try the service once and never build the habit. Retention work aimed at month three is aimed too late.

**Cross-product use is protective.** Members using only the delivery product churn at a materially higher rate than members using both delivery and rides; dual-product members churn least.

## Method

- **Data**: a simulated dataset supplied with the course, two tables — `members` (demographics, membership status, purchase behaviour) and `transactions` (user id, location, order type, amount, timestamps). Simulated, not real customer data.
- **Tools**: Excel for shaping, Tableau for every view.
- **Views built**: churn rate by segment, value tiering, platform/product mix, regional distribution, conversion funnel by order sequence, Recency × Frequency scatter, and a revenue-versus-recency view used to isolate high-value members at risk.

## Repository layout

```
deck/      Uber_One_Retention_Analytics.pptx   the presented deck
docs/      behavioral-churn-walkthrough.md     walkthrough of the Recency x Frequency analysis
tableau/   uber_one_dashboards.twbx            packaged workbook (data + images embedded)
           churn_rate.twb                      churn-rate worksheet
data/      uberone_members_transactions.xlsx   the simulated dataset (members, transactions)
figures/   churn-analysis.jpg
```

`.twbx` is a packaged Tableau workbook — open it in Tableau Desktop or Tableau Public and the data comes with it. `.twb` expects the dataset to be pointed at manually.

## Honest limitations

1. **The dataset is simulated.** The patterns are internally consistent and the method transfers, but no conclusion here is a statement about a real business.
2. **Observational, not causal.** Rising recency predicts churn in this data; nothing here establishes that a recency-triggered intervention would *cause* members to stay. That needs a holdout test.
3. **The recommendations are proposals.** Seasonal offers, category incentives, second-order nudges and tiered recall campaigns were designed as part of the coursework. None was deployed, and no retention lift is claimed.
4. **Recency and frequency are measured at a single cut-off**, not as rolling windows, so a member's position reflects the snapshot date rather than a trajectory.

## License

MIT for the analysis and documentation in this repository — see [LICENSE](LICENSE). The simulated dataset was provided as course material and is included for reproducibility only.
