---
id: attendee-tools-financial-freedom-number-calculator
title: Financial Freedom Number Calculator
type: attendee-tool
status: planned
confidence: verified
source: Prospa Excel workbook supplied by Audrey Li, 2026-09-29
as_of: 2026-09-29
owner: unassigned
tags: [08-channels-and-playbooks, attendee-tools, calculator, financial-freedom]
---

# Financial Freedom Number Calculator

## Purpose

An illustrative calculator to frame the capital goal required for work to become optional. Users enter assumptions in the green cells in the original workbook. It is not a retirement forecast or personal advice.

## User assumptions

| Input | Default value in supplied workbook | Guidance |
|---|---:|---|
| Current age | 40 | Your age today. |
| Age you would like work to become optional | 55 | Choose your target. |
| Desired annual lifestyle in today’s dollars | $120,000 | Annual spending you want your portfolio to support. |
| Current accessible investments outside super | $300,000 | Exclude your home and super for this illustration. |
| Annual amount directed to accessible investments | $30,000 | What you expect to invest each year. |
| Assumed annual investment return | 6% | Illustrative only. Returns are not guaranteed. |
| Assumed inflation rate | 2.5% | Used to convert your lifestyle target to future dollars. |
| Illustrative withdrawal rate | 4% | Planning assumption only, not a safe or guaranteed rate. |

## Illustrative calculations

Let:

- `current_age` = current age
- `target_age` = age work becomes optional
- `lifestyle_today` = desired annual lifestyle in today’s dollars
- `accessible_investments` = current investments outside super
- `annual_investment` = annual amount invested
- `return_rate` = assumed annual investment return
- `inflation_rate` = assumed inflation rate
- `withdrawal_rate` = illustrative withdrawal rate

| Output | Formula from supplied workbook |
|---|---|
| Years until target age | `max(target_age - current_age, 0)` |
| Lifestyle target at target age | `lifestyle_today × (1 + inflation_rate) ^ years_until_target_age` |
| Illustrative capital target | `lifestyle_target_at_target_age ÷ withdrawal_rate` when withdrawal rate is greater than zero |
| Projected accessible investments at target age | `accessible_investments × (1 + return_rate) ^ years + annual_investment × (((1 + return_rate) ^ years - 1) ÷ return_rate)`; if return rate is zero, the annual-investment component is `annual_investment × years` |
| Illustrative funding gap / surplus | `projected_accessible_investments - illustrative_capital_target` |
| Progress toward capital target | `projected_accessible_investments ÷ illustrative_capital_target` when the target is greater than zero |

## Question behind the number

> If your target age is earlier than the age at which you can access super, the issue is not only “How much wealth do I need?” It is also “Where does that wealth need to sit, and when must it be accessible?”

## Important limitations

This calculator is a simplified educational illustration. It ignores tax, fees, investment volatility, sequencing risk, changes in spending, superannuation, pensions, other assets and many other factors.

The assumed withdrawal rate is not a recommendation or guarantee. Personal financial advice should consider the user’s full circumstances.

## Source note

The supplied workbook cites Moneysmart guidance that retirement needs vary by desired lifestyle, and that planning should consider when super can be accessed and how income gaps may be funded.

- https://moneysmart.gov.au/plan-for-your-retirement
- https://moneysmart.gov.au/plan-for-your-retirement/super-and-pension-age-calculator
