# ThinkGuard: Preliminary Results on Overthinking in Code Generation

ThinkGuard is a collaborative research project on when a language model has reasoned enough to produce a correct program. Our long-term goal is to reduce reasoning-token use while preserving or improving the rate at which generated programs pass the judge. This summary presents the first-stage analysis of Qwen3-32B on LiveOIBench competitive programming problems.

## Preliminary results

We grouped runs by the original full-reasoning verdict and counted how often generating code from a shorter reasoning trace yielded an accepted solution.

| Original verdict | Cases evaluated | Became accepted | Share |
| --- | ---: | ---: | ---: |
| Wrong answer | 119 | 13 | 10.9% |
| Memory limit exceeded | 40 | 9 | 22.5% |
| Runtime error | 508 | 3 | 0.6% |
| Time limit exceeded | 132 | 0 | 0.0% |

Shorter traces sometimes recovered failures, particularly wrong answers and memory-limit failures. Across runs that were already accepted, truncating very early often reduced the acceptance rate. The results suggest that the value of additional reasoning varies across runs.

These figures describe a retrospective experiment on one model and benchmark. They do not estimate the net pass-rate change or token savings of a deployed early-stopping policy.

## Project status

The first-stage analysis is complete. We are training and evaluating an initial verifier to estimate when the model has enough information to stop, and will measure acceptance rates alongside reasoning-token use.
