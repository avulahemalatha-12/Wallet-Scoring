# Wallet Credit Scoring

This project scores DeFi wallet addresses based on historical interactions with the Aave V2 protocol. It assigns each wallet a credit score from **0 to 1000**, where higher scores indicate responsible and reliable behavior.

---

## 🔍 Objective

Build a behavioral credit scoring system for Ethereum wallets using Aave V2 transaction data.

---

## 📦 Dataset

* Source: Provided JSON file `user-wallet-transactions.json`
* Size: 100,000+ transaction records
* Actions included: `deposit`, `borrow`, `repay`, `redeemunderlying`, `liquidationcall`

Each record contains wallet activity, asset type, amount, price, and timestamps.

---

## ⚙️ Features Engineered

For each wallet, we compute:

| Feature                         | Description                                  |
| ------------------------------- | -------------------------------------------- |
| num\_deposit, num\_borrow, etc. | Count of actions                             |
| usd\_deposit, usd\_borrow, etc. | Total USD per action                         |
| repay\_to\_borrow\_ratio        | Measures repayment responsibility            |
| liquidation\_rate               | Fraction of borrows ending in liquidation    |
| avg\_time\_diff\_secs           | Avg. time between transactions               |
| unique\_assets\_used            | Number of unique asset types interacted with |

---

## 🧠 Scoring Logic

Wallets are scored with a base score of 500. Adjustments are applied as follows:

### Positive Behavior (+):

* `+150` for `repay_to_borrow_ratio > 0.8`
* `+100` for `num_deposit > 5` and `usd_deposit > 1000`
* `+100` for using >3 unique asset types

### Risky Behavior (−):

* `−200` for `liquidation_rate > 0.5`
* `−100` for `avg_time_diff_secs < 300` (bot-like)

Final score is capped between **0 and 1000**.

---

## 🛠️ How to Run

1. Upload `user-wallet-transactions.json` in Colab
2. Run the notebook `wallet_scoring_model.ipynb`
3. Outputs:

   * `wallet_scores.csv`: Wallet address + score
   * `score_distribution.png`: score_distribution of score ranges

---

## 📊 Score Ranges

| Range    | Behavior                  |
| -------- | ------------------------- |
| 0–200    | Very risky / bot-like     |
| 201–400  | Inconsistent or high risk |
| 401–700  | Normal users              |
| 701–900  | Responsible, experienced  |
| 901–1000 | Ideal, high-value users   |

---

## 📁 Files

* `wallet_scoring_model.ipynb`: Full pipeline
* `wallet_scores.csv`: Output scores
* `score_distribution.png`: Visualization
* `Readme.md`: Project overview
* `Analysis.md`: Score insights & behaviors

---

## 🔧 Requirements

```
pandas
matplotlib
```

---

## 📫 Contact / License

MIT License. Feel free to fork, modify, and share.
