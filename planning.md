# Project plan

## Product vision
A driver hears and sees an understandable warning, learns the likely consequence and safe immediate action, and can ask follow-up questions grounded in the correct vehicle manual. The demo uses simulated vehicle events and runs the time-sensitive warning path on QNX 8.0.

## Primary users and jobs
| User | Need | Success |
| --- | --- | --- |
| Driver in motion | Understand urgency without distraction | Short spoken alert and clear stop/continue guidance from deterministic policy |
| Driver safely parked | Locate a check or decide to call help | Vehicle-specific instructions with manual citation and escalation |
| Driver using voice | Ask a follow-up without navigating menus | Context-aware answer tied to current warning and manual |
| Reviewer | Reproduce and inspect QNX use | QEMU instructions, source references, observed output and video |

## Scope and boundaries
MVP scenarios: low tyre pressure/flat tyre, coolant temperature, low oil pressure, and brake system warning. Inputs are simulated, with a defined schema and vehicle profile. Warnings are not diagnoses. No vehicle control, live OBD integration, unrestricted web search, or safety certification is claimed.

## Architecture
1. QNX warning service receives WarningEvent and reads VehicleProfile.
2. WarningPolicy maps code and context to urgency, immediate action, and whether detailed interaction is allowed. It works without the LLM/network.
3. GuidanceService retrieves approved sections from ManualSource and prepares cited context.
4. An optional LLM explains approved context and answers follow-ups. Output is checked against policy and citations; unsupported answers fall back to a fixed message.
5. VoiceInterface provides speech input/output; screen shows the same action, source and escalation. AuditRecord logs code, rule, source, response, timing, and fallback without sensitive speech by default.

The first alert is deterministic. Retrieval, LLM and speech can fail independently without blocking it. Define measurable latency and fault behavior after the QNX baseline is running.

## Delivery increments
| Sprint | Goal | Evidence |
| --- | --- | --- |
| 0: foundation | QNX SDP 8.0/QEMU setup and tiny running service | Build log, target output, reproducible instructions |
| 1: warning path | Event schema, policy, four scenarios, screen/console alert | QNX demo of urgency and fallback |
| 2: manual guidance | Profile selection, PDF extraction/index, citations, safe missing-source behavior | Correct edition/page references and source tests |
| 3: conversation | Voice input/output, context-aware follow-ups, parked-state behavior | Recorded end-to-end QNX demonstration |
| 4: submission | UX polish, resilience, evidence, video and Devpost materials | Public reproducible repo and submission checklist |

## Backlog ordering
Issues are the source of truth for implementation. Build the QNX vertical slice before model integration. Split an issue if it cannot be reviewed in one increment. Review the backlog after each increment and adjust based on observed QNX constraints.

## Acceptance and release gates
- Driver guidance is understandable, short when moving, and includes a clear action.
- Unknown signal, missing manual, conflicting source, unavailable model, and speech failure lead to predictable safe messages.
- Manual-specific claims identify source title/edition/page. The UI never presents simulated data as real telemetry.
- Source and instructions reproduce the QNX 8.0 target build/run path; demo footage shows it working.
- Public repo, license, English description, category, video, and dates match the official rules. Submit only after evidence is reviewed.

## Risks and decisions
| Risk | Mitigation |
| --- | --- |
| QNX toolchain access/setup | Establish QEMU baseline first; record exact version and environment |
| Manual copyright/model mismatch | Use permissioned sample or authored mock manual; require explicit profile/edition |
| LLM hallucination or latency | Deterministic warning policy; cited retrieval; safe fallback and time limit |
| Voice distraction | Brief motion-mode alert; detailed Q&A when parked |
| Deadline | Preserve a functioning QNX core before optional voice/model polish |
