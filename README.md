# econ5200-lab09-ab-testing
# Diagnosing Experimental Failures in A/B Testing

## Objective
I investigated common problems in A/B testing, including faulty variance reduction, sample ratio mismatch, interference, Bayesian decision-making, and repeated testing.

## Methodology
- Debugged three bugs in an analyst's CUPED code and compared variance reduction and standard errors before and after fixing them.
- Ran sample ratio mismatch (SRM) chi-squared tests on two experiments with 100,000 and 20 million users.
- Simulated a marketplace with limited inventory to measure how interference affects the naive ATE compared with the global rollout effect.
- Ran a Bayesian A/B test using probability of improvement and expected loss, then compared the results with a permutation test.
- Wrote a reusable function for Bayesian A/B testing and tested it with four times the original sample size.
- Simulated 1,000 experiments with no true effect to compare false positive rates when checking results 50 times versus testing once at the end.

## Key Findings
- **CUPED:** Fixing three bugs increased variance reduction from 0.0% to 82.7% and reduced the standard error from 0.1539 to 0.0641.
- **Sample Ratio Mismatch:** A 0.600 percentage-point imbalance among 100,000 users produced a chi-squared statistic of 14.40, while a 0.050 percentage-point imbalance among 20 million users produced 20.00. Both triggered the SRM alarm, showing that large samples can make small imbalances statistically significant.
- **Interference:** The naive ATE was 0.1861, compared with 0.1428 for a global rollout. This overstated the rollout effect by 23.3% of the naive estimate because treated buyers competed with control buyers for limited inventory.
- **Bayesian A/B Testing:** The probability that B outperformed A was 0.8866, with an expected loss of 0.000473 from shipping B. The ship rule recommended not shipping B, and the permutation test gave a p-value of 0.2302.
- **Larger Sample Test:** With four times the users, the probability that B outperformed A increased to 0.9951, and the ship rule recommended shipping B.
- **Repeated Testing:** Checking results 50 times increased the false positive rate to 32.4%, compared with 5.3% for a single test at the end. Bonferroni correction reduced the rate to 1.9%.
