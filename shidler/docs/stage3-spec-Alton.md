# Stage 3 – Technical Specification  

---

## 1. Problem Statement

The firm is a pharmaceutical exporter with a **foreign-currency receivable of EUR 8,000,000** due in the future. The agreed forward rate is **1.0890 USD/EUR**, and settlement occurs at a fixed maturity date. The primary risk is that the euro may depreciate against the U.S. dollar before settlement, reducing the USD value of the receivable.  

An adverse exchange rate movement directly impacts revenue and profitability when converted into USD. The objective of the model is to evaluate hedging strategies that stabilize or improve USD proceeds while managing cost and risk exposure.

---

## 2. Inputs (Known Variables)

| Named Range | Description | Value | Unit | Source |
|------------|------------|-------|------|--------|
| FC_AMT | Foreign-currency receivable | 8,000,000 | EUR | Scenario |
| S0_in | Spot rate at inception | 1.0850 | USD/EUR | Market |
| F0_in | Forward rate | 1.0890 | USD/EUR | Scenario |
| R_USD | USD interest rate | 5.00% | Annual % | Assumed |
| R_FC | EUR interest rate | 3.00% | Annual % | Assumed |
| K_PUT | Put option strike | 1.0800 | USD/EUR | Assumed |
| K_CALL | Call option strike | 1.1000 | USD/EUR | Assumed |
| PREM_PUT | Put premium per EUR | 0.0200 | USD | Assumed |
| PREM_CALL | Call premium per EUR | 0.0150 | USD | Assumed |
| T_DAYS | Days to settlement | 180 | Days | Scenario |

---

## 3. Assumptions & Constraints

The model assumes a **simple interest rate framework using ACT/360 convention** for both USD and EUR calculations. Transaction costs, bid-ask spreads, and credit risk are excluded.  

Forward and money market hedges are assumed to satisfy **interest rate parity**, meaning outcomes should be approximately equivalent when markets are efficient.  

Options are European-style and only exercised at maturity. Premiums are paid upfront and treated as sunk costs.  

No taxes, accounting adjustments, or liquidity constraints are included in the model.

---

## 4. Calculation Flow

### Forward Hedge  
The exporter locks in the forward rate and converts the full receivable at maturity. USD proceeds are calculated by multiplying FC_AMT by F0_in. This eliminates all exchange rate uncertainty.

### Money Market Hedge  
The exporter borrows the present value of the EUR receivable by discounting FC_AMT using the EUR interest rate over the settlement period. The borrowed EUR is immediately converted to USD at the spot rate and invested at the USD interest rate. At maturity, the EUR receivable repays the loan, and the USD investment grows to its final value.  

### Option Hedge (Put Option)  
The exporter purchases a put option to guarantee a minimum exchange rate. If the spot rate at maturity is below the strike, the option is exercised. If the spot rate is above the strike, the exporter sells at market. Net proceeds equal the final USD conversion minus the premium cost.

### Option Hedge (Collar Strategy)  
A collar combines a purchased put and a sold call. The put provides downside protection while the call limits upside potential. Premium costs are partially offset. The payoff depends on whether the final spot rate is below the put strike, between strikes, or above the call strike.

---

## 5. Outputs

The model produces the following outputs:

- **USD Proceeds by Strategy** including forward, money market, and option hedges  
- **Comparison Table** showing net proceeds under each hedge  
- **Sensitivity Table** displaying USD outcomes across a range of exchange rates  
- **Strategy Performance Chart** illustrating payoff profiles for each hedge relative to spot rate changes  

---

## 6. Model Review — What Worked & Improvements

The Stage 2 model correctly implemented core hedging strategies and produced consistent results across forward and money market hedges. The structure allowed for basic comparison of strategies and clear visualization of outcomes.  

However, several improvements are needed. Naming conventions were not consistently applied, making the model less transparent. Some calculations relied on hardcoded values instead of dynamic inputs, reducing flexibility. The layout could be improved by separating inputs, calculations, and outputs more clearly.  

A refined version should standardize named ranges, improve formula clarity, and include automated scenario analysis. Additional metrics such as break-even exchange rates and cost efficiency comparisons would strengthen decision making.

---

## 7. Sensitivity Plan

Exchange rate scenarios are constructed within a **±5% range** around the initial spot rate. The step size is evenly distributed across the range to produce multiple scenarios for comparison.  

The sensitivity analysis shows how USD proceeds change under each hedging strategy as the exchange rate fluctuates. This allows direct comparison of downside protection and upside potential across strategies, highlighting trade-offs between risk and return.

---

## 8. Limitations & Next Steps

The model does not include dynamic hedging strategies, counterparty risk, or accounting treatment such as hedge accounting rules. It also assumes constant interest rates and ignores market frictions.  

Future improvements include integrating stochastic exchange rate simulations, adding transaction costs, and expanding option strategies.  

This specification will serve as the foundation for Stage 4, where an AI-generated model will be built using standardized inputs, structured calculation flow, and clearly defined outputs.

---
