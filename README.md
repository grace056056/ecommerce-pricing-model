# E-commerce Pricing Model

**Should an online store raise prices, cut back on discounts, or both?**

An Excel model that answers this question using six months of order data. It builds revenue and contribution margin by product category, compares four pricing scenarios, and tests how sensitive the result is to its assumptions.

- **[Download the model (.xlsx)](ecommerce_pricing_model.xlsx)**
- **[One-page summary (.pdf)](pricing_model_summary.pdf)**

---

## Result

| Scenario | Net revenue | Contribution | Change vs base |
|---|---|---|---|
| Base case | $104,920 | $45,584 | – |
| Trim discounts by half | $103,720 | $46,304 | +$720 (1.6%) |
| Raise list prices 5% | $101,964 | $47,003 | +$1,418 (3.1%) |
| Both | $100,338 | $47,403 | +$1,819 (4.0%) |

Six months, January to June 2024, completed orders only.

## What the data shows

- Discounts cost $4,642 over six months, or 4.2% of list value, across 30% of orders.
- Discounted orders are not bigger: 1.34 units per order with a discount, 1.35 at full price.
- Cancelled and refunded orders ($50,723) are excluded, so all revenue figures are net.

## Recommendation

1. **Cap discounts first, as a test on part of the traffic.** Discounts do not increase order size in the data, and trimming them has the smallest downside if the assumptions are wrong.
2. **Hold the 5% price rise until price sensitivity is measured.** It pays off as long as unit sales fall by less than 10.1% (the model expects 7.2%), but it loses money if customers are 1.5 times as price sensitive as assumed.
3. **Run a small price test per category**, then re-run the model with measured elasticity and real cost data.

---

## How the model works

| Tab | What it does |
|---|---|
| **Summary** | Scenario comparison, findings, recommendation, and chart |
| **Assumptions** | Every input in one place. Blue cells can be changed; yellow cells are assumptions that do not come from the data |
| **Baseline** | Units, list value, net revenue, and discounts by category, summed from the raw orders with `SUMIFS` |
| **Scenarios** | The same calculation repeated for each scenario |
| **Sensitivity** | Change in contribution across a range of price changes and levels of price sensitivity, plus a break-even calculation |
| **Data** | 3,500 order lines |

The calculation for each category:

1. **New net price** = list price × (1 + price change) × (1 − remaining discount rate)
2. **New units** = baseline units × (1 + elasticity × % change in net price)
3. **Contribution** = revenue − cost of goods − payment fees

Every number in the workbook is a formula. Change an input on the Assumptions tab and the Summary updates.

## Assumptions and limits

- **Cost of goods, price elasticity, and the payment fee are illustrative assumptions.** The dataset has no cost data and cannot measure elasticity. These inputs are marked in yellow, and the Sensitivity tab shows how much the result depends on them.
- **The data cannot show whether discounts bring in orders that would not otherwise happen.** It only shows that they do not increase order size.
- **The dataset is synthetic.** It is the sample dataset from [Insight Copilot](https://github.com/grace056056/insight-copilot), so the result demonstrates the method rather than a real store's economics.

---

Built by Tongyu (Grace) Wu · UCI Data Science · 2026
