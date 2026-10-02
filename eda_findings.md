# EDA Findings - Retail Customers

## Key insights

1. **Revenue is concentrated in Electronics.** It is 23% of orders but 57% of revenue; the top three categories bring in 82%.
2. **Membership drives spend.** Median order value: Basic Rs 9,154, Silver Rs 12,430, Gold Rs 13,967 (Gold is 1.5x Basic). Gold members also visit more (4.7 vs 3.2 per month).
3. **Returns are a Clothing problem.** Clothing return rate is 14.4% versus 6.1% overall and 3.0% in Beauty.
4. **Cash on Delivery customers are less satisfied** (3.37 vs 3.65 for other methods).
5. **Revenue peaks late in the year, but part of the peak is one big order.** December is the best month and Q4 delivers 30% of annual revenue (an even split would be 25%). Excluding the top 1% of orders, Q4 is 27%, so the seasonal lift is real but modest; a single Rs 531,422 order on 20 Dec inflates December. Order counts do not rise in Q4 - the lift comes from higher average order value.
6. **Customer value varies by city.** Average income is highest in Mumbai (Rs 1,002,646) and lowest in Nashik (Rs 764,595); Gold share ranges from 14% (Nashik) to 39% (Mumbai).
7. **Income tracks age (r = 0.75) but only weakly predicts order size** (Spearman r = 0.23); what you buy and your membership tier matter far more than income.

## Conclusions

The data describes a retail business whose revenue depends heavily on one category, whose
best customers are loyalty members, and whose main leaks are product returns and a weaker
cash-on-delivery experience. Spending is highly skewed: most orders are modest, while a
small number of large Electronics orders carry a disproportionate share of revenue, so
medians describe the typical customer better than means.

## Recommendations

1. **Protect and grow Electronics, but reduce the dependence on it.** Electronics gives
   57% of revenue. Prioritise stock availability and warranty/EMI offers there, and
   cross-sell Home & Kitchen and Beauty to Electronics buyers to broaden the base.
2. **Invest in the membership ladder.** Gold members spend more per order and visit more
   often. Offer targeted upgrades to high-income Silver customers, and consider welcome
   benefits for Basic members in cities where the Gold share is low.
3. **Fix Clothing returns.** A 14% return rate is several times the other categories.
   Improve size guides and product photos, add fit/size reviews, and check the return reasons.
4. **Improve the cash-on-delivery experience.** Lower satisfaction suggests delivery or trust
   friction. Nudge COD customers to UPI with small incentives and audit COD delivery times.
5. **Plan for a modest Q4 lift.** Q4 brings 30% of revenue (27% without the top 1%
   of orders), driven by bigger baskets rather than more orders. Stock high-ticket items and
   bundles ahead of October, and test off-season promotions on the slower months.
6. **Use discounts selectively.** Discounts correlate only weakly with satisfaction, so deep
   discounts are not a reliable way to improve experience; reserve them for peak events and
   slow categories.

## Limitations

- The file contains a few missing values (income, visits, satisfaction); EDA ignores them.
- Correlation is not causation, and one year of data cannot show whether seasonality repeats.
- Group differences should be validated with significance tests before large investments.
