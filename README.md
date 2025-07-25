# Wallet-Risk-Scoring-From-Scratch
 Repository Purpose
This repository is dedicated to scoring wallet IDs based on transactional behavior, using Python. It reads wallet IDs from a CSV, fetches their transactions, and calculates a custom risk score for each wallet. The final output is stored in a structured format for further analysis or visualization.

📊 Explanation
# Data Collection Method
The dataset was initially imported from a CSV file named Wallet id - Sheet1.csv, which contains a list of wallet addresses under the column wallet_id.
Transactions were simulated or fetched via a placeholder function get_wallet_transactions(wallet_id) assuming access to blockchain or transaction history.

# Feature Selection Rationale
We analyzed the following key features for scoring:

Number of Transactions: High frequency may indicate bot activity or operational wallets.

Average Transaction Amount: Extremely high or low amounts can signify suspicious behavior.

Transaction Count per Unique Address: A high concentration of interactions with a single address may indicate laundering patterns.

Ratio of Incoming to Outgoing Transactions: An imbalance may imply storage-only or drain wallets.

Time Gap Between Transactions: Short gaps can indicate automated or batch activity.

 # Scoring Method
 
Each wallet's behavior is assessed using the above features and given a risk score between 0 and 1000.
The scoring follows a custom logic-based rule where risk increases with:

Fewer transactions (inactive wallets may be at higher risk).

Very high transaction values (outliers).

Repetitive interaction with a single address.

Suspicious transaction timing patterns.

The score is normalized and capped to ensure consistency and interpretability.
final_score = min(int(risk_score * weight_factor), 1000)

 # Justification of Risk Indicators Used
 
These indicators are inspired by common blockchain risk patterns observed in fraudulent or manipulative wallets:

Low diversity in interactions can hint at shell wallets or mixers.

High transaction amounts may represent attempts to bypass thresholds.

Short intervals between transactions are a red flag for bot activity.

High inflow without outflow can indicate dormant or stash wallets potentially linked to illegal holding.
