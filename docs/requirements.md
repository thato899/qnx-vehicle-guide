# Requirements and traceability

Source: https://qnx.devpost.com/ and https://qnx.devpost.com/rules (reviewed 25 November 2026). Official rules prevail if challenge copy differs.

## Hackathon gates
| ID | Requirement | Planned evidence |
| --- | --- | --- |
| H1 | Working application/component on QNX 8.0 or host tool supporting QNX 8.0 | QNX service built and run under QEMU |
| H2 | Automotive & Mobility category selected | Devpost form |
| H3 | New project during 2 Nov–15 Dec 2026 or significantly updated then | Git history and description |
| H4 | Public GitHub/GitLab/Bitbucket repo, source/assets, visible open-source license | Repository root and About panel |
| H5 | QNX version, target and toolchain in build/run instructions | README and observed commands |
| H6 | Real QNX evidence, with files/functions/output identified | QNX-specific implementation and demo |
| H7 | Public YouTube demo under three minutes showing function on intended target | Video URL |
| H8 | English description explaining features/functionality | Devpost description |
| H9 | Free, unrestricted judging access through judging period | Public repo and reproducible simulation |
| H10 | Original work, authorized third-party assets/integrations | Attribution/license inventory |

## Product requirements
| ID | Driver outcome | Acceptance signal |
| --- | --- | --- |
| P1 | Understand a warning quickly | Short spoken/on-screen meaning, urgency and immediate action |
| P2 | Know whether to check or call help | Deterministic escalation for supported codes and unknown-code fallback |
| P3 | Find the right place on their vehicle | Matching profile and cited manual section/diagram; no invented locations |
| P4 | Ask follow-up questions by voice | Current-warning context, manual citation, understandable clarification |
| P5 | Avoid distraction while moving | Only brief urgent guidance while in motion; detail after parking |
| P6 | Continue receiving alerts when AI/offline services fail | QNX policy emits immediate fixed alert without LLM or network |
| P7 | Understand uncertainty | Explicitly distinguish warning interpretation from diagnosis |

## Nonfunctional targets
Define timing budgets through measurement on QNX QEMU after Sprint 0; record input-to-alert latency and degraded behavior. Keep warnings independent from external API availability. Log enough to reproduce a simulated decision while minimizing stored speech and personal data. Make the screen readable and provide both voice and text.
