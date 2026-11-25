# QNX Vehicle Guide

A planned QNX 8.0 Automotive & Mobility hackathon project: turn simulated dashboard warnings into timely, understandable actions, grounded in a selected vehicle manual, with voice follow-up questions.

**Status: planning. No working QNX application or voice assistant is implemented yet.** See [status.md](status.md).

## Driver experience
1. A simulated warning arrives with vehicle profile and motion state.
2. A deterministic QNX warning policy announces urgency and immediate action. It does not wait for an LLM or internet.
3. A permissioned manual supplies vehicle-specific checks, locations and citations.
4. The driver can ask follow-up questions by voice. Detailed guidance is deferred until parked. An optional LLM explains retrieved manual passages and is constrained by the warning policy.
5. Missing or uncertain information produces an explicit fallback and advice to contact appropriate help.

Initial scenarios: tyre pressure/flat tyre, engine overheating, oil pressure, and brake fault. The demo is advisory and uses simulated signals; it is not a diagnostic, repair, vehicle-control, or certified safety system.

## Architecture and development
See [planning.md](planning.md) for increments and object boundaries, [docs/requirements.md](docs/requirements.md) for hackathon/product traceability, [AGENTS.md](AGENTS.md) for contributor rules, and [status.md](status.md) for honest progress. GitHub issues define reviewable user stories and acceptance criteria.

## Build and run
Not yet available. Sprint 0 must establish QNX SDP 8.0, the exact toolchain version, QEMU target image, commands to build and run the service, and observed output. Do not infer QNX compatibility from this README.

## Hackathon submission
The QNX Global Hackathon deadline is **15 December 2026, 21:00 SAST**. The submission requires this public open-source repository, a functional QNX 8.0 target and reproducible instructions, one Automotive & Mobility category selection, English description, explicit QNX evidence, and a public YouTube demo under three minutes. Refer to the [official rules](https://qnx.devpost.com/rules) before submission.

## License
MIT. Third-party manuals, QNX SDK components, speech/LLM dependencies and media retain their own licenses and must not be redistributed without permission.
