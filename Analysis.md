# Credit Score Analysis

This analysis provides insights into the distribution and behavior of wallets based on their credit scores computed from Aave V2 transaction data.

---

## 📈 Score Distribution

Wallets were binned into score ranges of 100 points. Here is a summary:

| Score Range | # Wallets                                                    | Description |
| ----------- | ------------------------------------------------------------ | ----------- |
| 0–100       | High-risk, likely liquidated or bots                         |             |
| 101–200     | Risky with little repayment behavior                         |             |
| 201–300     | Low diversity, frequent borrowing without repayment          |             |
| 301–400     | Slightly better usage but still inconsistent                 |             |
| 401–500     | Average DeFi users, balanced behavior                        |             |
| 501–600     | Regular users with responsible borrowing                     |             |
| 601–700     | Rarely liquidated, some asset diversity                      |             |
| 701–800     | Active with solid repayment history                          |             |
| 801–900     | High-value users with diverse interactions                   |             |
| 901–1000    | Ideal users: high repayment, low liquidation, high diversity |             |

*Visualized in `score_distribution.png`*

---

## 🔍 Behavior of Low-Scoring Wallets (0–300)

* Often show:

  * High `liquidation_rate`
  * Very low `repay_to_borrow_ratio`
  * Minimal `deposit` activity
  * Very fast or bot-like transactions (`<300s`)

These may be:

* Bot-operated accounts
* Wallets used to exploit incentives without maintaining positions

---

## 🌟 Behavior of High-Scoring Wallets (800–1000)

* Display:

  * High diversity in `assetSymbol`
  * Regular deposits and redemptions
  * High `repay_to_borrow_ratio` (>0.8)
  * Almost zero `liquidation_rate`

These wallets indicate:

* Strategic long-term users
* Possibly institutional participants or experienced DeFi users

---

## 📌 Insights

* **Repayment behavior** is the most indicative of creditworthiness
* **Liquidation events** sharply reduce score
* **High score users** tend to interact with 3–7 asset types and have spaced-out transactions

---
