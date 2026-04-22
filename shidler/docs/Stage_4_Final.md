# Stage 4 – Final Analysis, Prompt Engineering, and Recommendation  
**Scenario 2: Pharma Exporter**  
**EUR Receivable: €8,000,000**  
**Forward Rate: 1.0890 USD/EUR**

## A. Exposure Summary

This firm is a pharmaceutical exporter with a foreign currency receivable of **€8,000,000**. Because the receivable will be converted into U.S. dollars at a future date, the company faces transaction exposure from changes in the EUR/USD exchange rate. If the euro weakens before settlement, the USD value of the receivable falls and the company collects fewer dollars than expected. If the euro strengthens, the company benefits from a higher USD conversion value.

The main concern is the effect of exchange rate movements on operating cash flow, planning, and financial performance. For a large receivable like this one, even relatively small FX changes can materially affect reported revenue and cash collections. Since this is a business exposure tied to a real export transaction, the hedging decision should focus on protecting expected dollar inflows while still considering cost, liquidity, and flexibility.

## B. Summary of Hedge Outcomes

### Forward Hedge

The forward hedge produces the highest degree of certainty because it locks in the future exchange rate today. In this case, the firm can lock in conversion at **1.0890 USD/EUR**, which gives guaranteed USD proceeds of:

**€8,000,000 × 1.0890 = $8,712,000**

This strategy is attractive when management values predictability and wants to remove exchange rate uncertainty from the decision entirely. The disadvantage is that the company gives up any benefit if the euro appreciates above the contracted forward rate.

### Money Market Hedge

The money market hedge creates a synthetic forward by borrowing the present value of the euro receivable, converting the amount to dollars at today’s spot rate, and investing those dollars until the receivable is collected. In theory, this result should be very close to the forward hedge because of covered interest parity.

The main difference is not the economic outcome, but the implementation. A money market hedge uses borrowing capacity and affects liquidity planning. This can matter if the firm wants to preserve financing flexibility or avoid balance sheet effects tied to short term borrowing.

### Put Option Hedge

A put option hedge provides protection against euro depreciation while preserving upside if the euro strengthens. This strategy gives the firm a minimum acceptable exchange rate while still allowing it to benefit from favorable market moves. That flexibility is the main advantage of the option hedge.

The drawback is the premium cost. Unlike the forward and money market hedge, the option is not free protection. Management must decide whether the value of upside participation is worth paying for. If the firm expects volatility and wants protection without fully giving up upside, the put becomes more attractive.

### Call Option Hedge

For a firm receiving euros in the future, a call option is generally not the primary hedge instrument because a call gives the right to buy foreign currency. This type of option is more naturally associated with hedging foreign currency payables rather than receivables. In this scenario, the call option is less relevant as a direct hedging recommendation, but it can still be modeled to compare payoff structure and understand how option positions differ.

### No Hedge

Choosing not to hedge leaves the firm fully exposed to exchange rate changes. This strategy has no upfront premium and no contractual restriction, but it also provides no protection. If the euro depreciates, the firm collects fewer dollars than expected. If the euro appreciates, the firm benefits. This is the highest risk strategy because the final USD proceeds depend entirely on the future spot rate.

## C. Sensitivity Interpretation

The sensitivity analysis helps show how each strategy performs across a reasonable range of future spot rates. In euro depreciation scenarios, the forward hedge performs well because it completely protects the receivable and fixes dollar proceeds at a known amount. The money market hedge should produce a similar result, which confirms that both strategies are economically close substitutes under normal market conditions. The put option also protects the firm in downside scenarios, but its net benefit is reduced by the premium cost.

In euro appreciation scenarios, the no hedge position generates the highest proceeds because the firm keeps full exposure to favorable exchange rate movements. The forward hedge does not improve when the euro rises, since the rate is already locked. The put option becomes more attractive in this range because it allows the firm to let the option expire and convert at the stronger market rate, keeping upside after accounting for the premium paid.

The main tradeoff is clear. The forward and money market hedges maximize certainty. The put option provides a balance between protection and flexibility. The unhedged strategy offers maximum upside but also creates the most risk.

## D. Strategic Recommendation

The strongest recommendation for this scenario is the **forward hedge**.

The reason is that this exposure comes from a real operating receivable, and the firm’s main concern should be protecting expected U.S. dollar cash inflows rather than speculating on currency movements. The forward hedge gives complete certainty and locks in **$8,712,000**, which supports better budgeting, performance measurement, and financial planning. It also avoids the premium cost of an option strategy.

A put option could also be justified if management has a stronger view that the euro may appreciate and is willing to pay for upside participation. However, for a pharmaceutical exporter managing a large known receivable, the forward hedge is the most practical and disciplined choice. It aligns best with the objective of reducing transaction risk and preserving operating certainty.

## E. Executive Justification

From a management perspective, the forward hedge is the most defensible strategy because it improves cash flow stability and simplifies decision making. The company knows exactly how many dollars it will receive, which helps with forecasting, internal budgeting, and performance targets. That certainty is valuable for a business that may already face uncertainty from pricing, production, regulation, and customer demand.

Compared with the money market hedge, the forward is simpler to execute and does not require borrowing or interim funding decisions. Compared with the put option, it avoids premium expense and delivers a guaranteed result immediately. Compared with remaining unhedged, it removes the possibility that a weaker euro will reduce reported revenue and operating cash flow.

For a large commercial receivable, risk reduction should usually take priority over trying to preserve upside from exchange rate gains. The forward hedge is the clearest strategy for meeting that objective.

## F. Structured AI Prompt

# GOAL

Create an Excel workbook that models FX hedging strategies for a foreign currency receivable. The workbook must evaluate forward hedge, money market hedge, put option hedge, call option hedge, and no hedge outcomes for a euro receivable and generate a sensitivity table showing results across a plus or minus 5 percent range of future spot rates.

# INPUT VARIABLES

Use the following named ranges exactly as written. Do not invent alternative naming conventions.

- `FC_AMT` = 8000000
- `F0_in` = 1.0890

Also include the following named ranges using the exact values from the Stage 2 spreadsheet:
- `S0_in`
- `R_USD`
- `R_FC`
- `K_PUT`
- `K_CALL`
- `PREM_PUT`
- `PREM_CALL`
- `T_DAYS`

All scenario specific variables must be explicitly entered in the input section. The AI must not infer missing values.

# INPUT SECTION AND FORMATTING

Build a clearly labeled input section at the top of the worksheet.

Apply color coding exactly as follows:
- **Yellow** for user inputs
- **Blue** for assumptions
- **Green** for formulas
- **Gray** for final outputs

Display both the variable name and value for each named range.

# MODEL LOGIC

## Forward Hedge
Calculate locked in USD proceeds using:
`Forward Proceeds = FC_AMT * F0_in`

## Money Market Hedge
Model the money market hedge in three steps:
1. Discount the euro receivable using the foreign interest rate and time to maturity
2. Convert the discounted euro amount to USD at spot
3. Invest the USD proceeds at the domestic interest rate until maturity

The final money market hedge result should be clearly displayed as net USD proceeds.

## Put Option Hedge
Model the put option as downside protection for the receivable.
- At maturity, compare the future spot rate to the put strike
- Use the option when the strike is more favorable than the market
- Subtract the total option premium cost from proceeds

## Call Option Hedge
Include a call option section for comparison.
- Show payoff logic based on the future spot rate and call strike
- Subtract the total premium cost
- Label clearly that this is included for comparative modeling purposes

## No Hedge
Calculate unhedged USD proceeds at each future spot rate:
`No Hedge Proceeds = FC_AMT * S_T`

# SENSITIVITY ANALYSIS

Create a sensitivity table using future spot rates over a plus or minus 5 percent range from the base spot rate.

For each future spot rate, show:
- No Hedge proceeds
- Forward Hedge proceeds
- Money Market Hedge proceeds
- Put Option Hedge proceeds
- Call Option Hedge proceeds

Make the table easy to compare visually and clearly label all columns and rows.

# VERIFICATION

Include explicit model checks:
1. Confirm that the forward hedge and money market hedge are approximately equal under covered interest parity
2. Confirm formula consistency across the sensitivity table
3. Confirm option payoff logic works correctly above and below strike prices
4. Confirm all formulas reference named ranges where applicable

# EXPORT

Generate a clean workbook suitable for executive review.
Use professional labels, readable spacing, and consistent formatting.
The sheet should be understandable without needing additional explanation.

## Extra Credit: Areas for Further Study and Improvement

One area for further study is how AI tools could automate this model beyond a one time spreadsheet build. A more advanced system could pull live spot rates, forward rates, and interest rates from market data sources and refresh the hedge analysis in real time. It could also run simulations across a much larger distribution of exchange rate outcomes rather than only a fixed sensitivity table. This would make the analysis more useful for treasury teams that need to update recommendations quickly as markets move.

Another important area is model governance through GitHub and reproducibility. By storing the spreadsheet, written specification, and structured prompt in the same repository, the firm creates a clear audit trail that shows how the hedge model was designed, updated, and justified. That kind of version control is valuable not only for finance teams but also for accounting and audit functions that may need evidence supporting hedge documentation, model consistency, and management review.
