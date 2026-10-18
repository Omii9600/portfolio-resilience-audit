# The Resilience Test: What Did Diversification Actually Protect?

A reproducible portfolio-risk investigation using 619,040 daily observations across 505 tickers from February 2013 to February 2018. It tests whether diversification reduced downside risk in a chronological holdout, and whether that result holds across portfolio breadth, rolling windows, rebalance frequency, and illustrative transaction-cost assumptions.

> Historical educational analysis only. Not investment advice. This dataset ends in 2018; it is not current-market research.

## Why this project is different

Instead of selecting eventual winners, this project asks whether broader portfolios reduced downside risk in a later holdout—and whether that finding persists across portfolio breadth, rolling windows, and cost assumptions. It makes ticker-screening choices, survivorship risk, adjustment uncertainty, and backtest simplifications visible. The central question is: **What did diversification protect in this sample, and how robust is that evidence?**

## Dataset

Input file: `all_stocks_5yr.csv`  
Observed in the supplied file: **619,040 rows, 7 columns, 505 tickers**. Date range: **2013-02-08 to 2018-02-07**. Fields: `date`, `open`, `high`, `low`, `close`, `volume`, `Name`. Missing values are limited to 11 `open`, 8 `high`, and 8 `low` entries; the return analysis relies on `close`.

For local use, put the CSV beside the notebook. In Kaggle, create a notebook, attach the CSV using **Add Input**, and edit `DATA_PATH` to the mounted input path shown in the Kaggle file browser. The notebook's coverage screen and common complete-case panel determine the analyzed universe; the exact ticker count is printed when you run it. Respect the original dataset's attribution and license; confirm those details on its source page before republishing any data.

## Repository layout

.
├── all_stocks_5yr.csv        # keep local; do not commit unless license permits
├── portfolio_resilience_audit.ipynb
├── requirements.txt
├── .gitignore
├── LICENSE
├── CITATION_AND_LICENSE.md
├── PROJECT_DESCRIPTION.md
├── MEDIUM_ARTICLE_DRAFT.md
└── images/                   # generated charts; notebook creates this folder

## Run locally

1. Create a Python 3.10+ environment.
2. Install dependencies: `pip install -r requirements.txt`
3. Put `all_stocks_5yr.csv` beside the notebook.
4. Open `portfolio_resilience_audit.ipynb` in Jupyter and run all cells.
5. Review outputs before writing numerical conclusions. Figures export to `images/`.

## Questions explored

- Does diversification reduce held-out downside risk as portfolio breadth increases?
- How do annualized volatility, maximum drawdown, historical 5% VaR and CVaR compare across portfolio constructions?
- Is any risk reduction stable across the held-out period and rolling 252-day windows?
- How sensitive are results to monthly versus quarterly rebalancing and illustrative turnover costs?
- How does capped inverse-volatility weighting compare with equal weighting?
- What do training-period correlations and constituent-versus-portfolio volatility reveal about diversification?

## Methods

Chronological 60/40 train-test split; ticker coverage screen; training-only liquidity selection; complete common return panel; close-to-close returns; equal-weight portfolios at multiple breadths; capped inverse-volatility portfolio; annualized metrics using 252 trading days; maximum drawdown; empirical 5% daily VaR/CVaR; rolling-window stability and cost/rebalance sensitivity. This is a transparent historical study, not production-grade execution backtesting.

## Important limitations

The file ends in 2018 and may omit delisted firms or historical index constituents, creating survivorship bias. Split- and dividend-adjustment status is unverified. The analysis uses a common complete-case panel, simplified rebalancing, and illustrative costs; it excludes taxes, bid-ask spreads, market impact, and executable trading. These limitations can materially change results. Do not present this as current-market research or investment advice.

## Results

Run the notebook and insert only findings supported by its outputs. Add selected figures from `images/` here, with descriptive captions and alt text. Do not commit conclusions or screenshots with fabricated or placeholder results.

## Medium article draft

### The Resilience Test: What Did Diversification Actually Protect?

Diversification is often described as a free reduction in risk. But how much protection does it provide in practice—and does that protection survive different market windows, portfolio sizes, and trading assumptions?

I examined 619,040 daily observations across 505 tickers from February 2013 to February 2018. Rather than selecting stocks by their eventual winners, I used a chronological split: training-period liquidity screened the candidate universe, and portfolio comparisons were evaluated on a later holdout. I compared equal-weight portfolios of different breadths with a capped inverse-volatility alternative.

**I measured resilience, not just return.** Held-out annualized volatility and maximum drawdown show the broad path of risk; empirical 5% VaR and CVaR focus on the weaker daily outcomes. The longest underwater spell adds a recovery-time perspective. *(Insert `images/02_test_wealth.png` and `images/03_test_drawdowns.png`.)*

**Then I challenged the result.** [Insert actual values from `summary` and `breadth_df`: which portfolio reduced downside risk, and what return trade-off came with it?] [State whether the relationship held across rolling windows.] Monthly versus quarterly rebalancing and illustrative turnover-cost assumptions help reveal whether a headline result depends on convenient assumptions. *(Insert `images/04_breadth_risk.png`, `images/05_rolling_stability.png` if available, and `images/06_cost_sensitivity.png`.)*

This is not proof that a particular portfolio will perform better in the future. The data ends in 2018; its split/dividend adjustment and survivorship status are unverified, and the cost model is simplified. Better point-in-time constituents, adjusted prices, and executable transaction-cost data could materially change the findings.

**Takeaway:** [After running the notebook, summarize one measured result, one important caveat, and the next dataset or test that could change the conclusion. Do not publish unverified numbers.]

*This article is for educational purposes and is not investment advice.*

## Publish responsibly

Do not upload the raw CSV to GitHub or re-host it on Kaggle unless the dataset license permits redistribution. Link to the original source, cite its author, and verify its license. The notebook can be published with the attached dataset input on Kaggle; include your own interpretation and acknowledge the source. Replace every bracketed article prompt with results from a successful notebook run before publishing.