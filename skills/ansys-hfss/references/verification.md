# Ansys HFSS | PyAEDT & Solver Validation: Verification worksheet

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

- [ ] Solution type and wave-port modes match the design problem.
- [ ] HFSS project has a completed, non-error, converged setup.
- [ ] Saved S-parameter files list correct port map and impedance.
- [ ] HFSS/CST comparison uses matched units, materials and calibration planes.

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

- https://aedt.docs.pyansys.com/version/stable/API/_autosummary/ansys.aedt.core.hfss.Hfss.create_setup.html
- https://aedt.docs.pyansys.com/version/stable/API/Setup.html
