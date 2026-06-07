# Cashflow Rate Calculator

A Python script to calculate monthly IRR, nominal annual rate (APR), and effective annual rate (EAR) for loan cashflow scenarios using `numpy_financial`.

---

## Formulas

### 1. Effective Annual Rate from APR

$$\text{EAR} = \left(1 + \frac{\text{APR}}{12}\right)^{12} - 1$$

Used when the nominal annual rate (APR) is known and you want to find the true annualized rate accounting for monthly compounding.

| Parameter | Description |
|-----------|-------------|
| `APR` | Annual Percentage Rate — the nominal yearly rate, not accounting for compounding |
| `12` | Number of compounding periods per year (monthly compounding) |
| `EAR` | Effective Annual Rate — the actual yearly return after compounding is applied |

---

### 2. Effective Annual Rate from Monthly IRR

$$\text{EAR} = (1 + r)^{12} - 1$$

Used when the monthly rate `r` is known directly (e.g. calculated via IRR) and you want to annualize it.

| Parameter | Description |
|-----------|-------------|
| `r` | Monthly interest rate (e.g. IRR computed from monthly cashflows) |
| `12` | Number of months in a year |
| `EAR` | Effective Annual Rate — the true annualized rate after compounding |

> **Note:** This is equivalent to the first formula since $r = \frac{\text{APR}}{12}$.

---

### 3. Fixed Installment (PMT)

$$\text{PMT} = P \times \frac{r \times (1 + r)^n}{(1 + r)^n - 1}$$

Calculates the fixed periodic payment required to fully repay a loan over `n` periods.

| Parameter | Description |
|-----------|-------------|
| `PMT` | Payment amount per period (e.g. monthly installment) |
| `P` | Principal — the initial loan amount |
| `r` | Periodic interest rate (monthly rate = APR / 12) |
| `n` | Total number of payment periods (e.g. 12 for a 1-year monthly loan) |

**Example:** A loan of 800,000,000 Tomans at a monthly rate of `r` over 4 months:

$$\text{PMT} = 800{,}000{,}000 \times \frac{r \times (1 + r)^4}{(1 + r)^4 - 1}$$

---

## Usage

```bash
uv run test3.py
```

### Example Output

```
نرخ سود ماهانه (IRR)     : 0.003500  (0.3500٪)
نرخ اسمی سالانه (APR)     : 4.20٪
نرخ موثر سالانه (EAR)     : 4.28٪
```

---

## Requirements

- Python 3.8+
- `numpy_financial`

Install with:

```bash
uv sync
```
