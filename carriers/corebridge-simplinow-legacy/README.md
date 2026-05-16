# Corebridge SimpliNow Legacy Max — Rate Reference

**Carrier:** Corebridge Financial (issued by American General Life Insurance Co., Houston, TX)
**Product:** SimpliNow Legacy Max — Level Death Benefit (Simplified Issue Whole Life)
**AM Best:** A
**Available:** All states except New York

## Premium Formula

```
monthly_premium = ((face / 1000) * rate_per_k + 36.87) * 0.087
```

- `face` — face amount in dollars
- `rate_per_k` — annual rate per $1,000 of face (looked up by gender/tobacco/age in `rates.json`)
- `36.87` — annual policy fee
- `0.087` — monthly modal factor

Verified to within $0.03 against 136 actual quote data points from the Corebridge Final Expense Quoter.

## Underwriting Limits

| | Non-Tobacco | Tobacco |
|---|---|---|
| **Issue ages** | 50 – 80 | 50 – 70 (max issue age 70) |

| Age band | Max face amount |
|---|---|
| 50 – 64 | $25,000 |
| 65 – 74 | $30,000 |
| 75 – 80 | $35,000 |

Minimum face amount: $5,000 (all ages).

## Riders

**Included at no extra cost:**
- Terminal Illness Accelerated Benefit Rider
- Nursing Home Confinement Rider

**Optional (additional cost):**
- Accidental Death Benefit Rider

## Data Source

5-year anchor ages (50, 55, 60, 65, 70, 75, 80) verified directly against Corebridge quote sheets. Intermediate ages are linear-interpolated between anchors (drift vs. the underlying exponential mortality curve is <0.5%).

## Example Calculations

| Profile | Face | Expected | Calculated |
|---|---|---|---|
| F-65 NT | $20,000 | $86.38 | $86.38 |
| M-70 T  | $25,000 | $289.63 | $289.63 |
| M-80 NT | $35,000 | $528.83 | $528.81 |
| F-75 NT | $10,000 | $79.33 | $79.33 |
