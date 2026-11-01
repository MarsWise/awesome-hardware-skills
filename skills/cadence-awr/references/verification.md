# Cadence AWR | Microwave & RF Circuit Design: Verification worksheet

## Input record

- Project path and version/commit:
- Application version and license:
- Imported libraries and models:
- Units and coordinate/reference system:
- Requirements and numerical thresholds:
- Native editable artifact location:

## Gate 0 — static/preflight

- [ ] Actual target software and required environment discovered
- [ ] Read-only inventory completed before changes
- [ ] Version/branch/copy created for edits
- [ ] Relevant options and APIs checked against installed version

## Gate 1 — application/tool execution

- [ ] Models and substrate valid in claimed frequency/power regime.
- [ ] Ports, reference impedances and calibration plane stated.
- [ ] Solver actually ran, with proper sweep bounds and output evidence.
- [ ] Small-signal S-parameter pass never substitutes for required nonlinear verification.

## Gate 2 — independent result

- [ ] Independent measurement/physical inspection done where applicable, or mark NOT_RUN
- [ ] Model/mesh/export sensitivity and uncertainty disclosed
- [ ] Every claimed number links to a saved log or machine-generated result
- [ ] Deliverable reopened/imported and compared to source revision

## Result table template

| Gate | Status (PASS / FAIL / BLOCKED / NOT_RUN) | Evidence path | Notes |
|---|---|---|---|
| L0 preflight | NOT_RUN | | |
| L1 tool verification | NOT_RUN | | |
| L2 independent physical check | NOT_RUN | | |

## Tool documentation

- https://www.cadence.com/en_US/home/tools/system-analysis/rf-microwave-design/awr-design-environment-platform.html
- Use the exact installed AWR Automation/Scripting Guide for working examples.
