---
name: cadence-awr
description: Use for Cadence AWR Design Environment and Microwave Office RF/microwave schematic, S-parameter and harmonic-balance analysis, EM co-simulation, circuit optimization and design rule review.
---

# Cadence AWR | Microwave & RF Circuit Design

## Use when

Use for Cadence AWR Design Environment and Microwave Office RF/microwave schematic, S-parameter and harmonic-balance analysis, EM co-simulation, circuit optimization and design rule review.

## Runtime discovery

- Native application: licensed Cadence AWR Design Environment / Microwave Office on an authorized desktop.
- Locate project, schematic hierarchy, substrate definition, stackup/technology files, measurement equations, tune/optimization settings and EM layout.
- AWR supports automation interfaces including scripting; exact languages, objects and entry points depend on release. Inspect the installed AWR scripting documentation and API browser first.
- The skill does not grant a generic `import awr` Python API; never invent it.

## Working procedure

1. Identify intended RF function, center frequency, bandwidth, required gain/return loss, P1dB/IP3/noise figure/PAE as applicable and allowable uncertainty.
2. Read projects and substrate definitions. Inspect port labels, reference impedance, device model versions, bias conditions, nonlinear model validity and measurement setup.
3. Establish a linear circuit baseline (S-parameters, stability factors, impedance matching). For nonlinear work, configure harmonic balance and spectral conditions appropriate to the model.
4. Validate EM model boundaries, substrate, via definitions, ports, de-embedding, mesh and circuit/EM co-simulation connectivity before optimization.
5. After approval, sweep one or more documented variables and compare actual simulator datasets against objectives; retain seeds/settings for yield and Monte Carlo runs.
6. Compare a passive structure with independent HFSS/CST or measured Touchstone when possible, matching reference planes and port order.
7. Export native project, measurement equations, Touchstone/CSV data and solver log; identify license-blocked analysis separately.

## Engineering checks

- Models and substrate valid in claimed frequency/power regime.
- Ports, reference impedances and calibration plane stated.
- Solver actually ran, with proper sweep bounds and output evidence.
- Small-signal S-parameter pass never substitutes for required nonlinear verification.

## Common verification and safety contract

## Non-negotiable practice

- **Read first, write with permission.** Identify installed application, release, OS, executable/API availability, license, project location, customer confidentiality, file version and requested outputs. Protect source by branch/copy; never silently edit the original.
- **No invented tool results.** Give statuses PASS, FAIL, BLOCKED or NOT_RUN. If a solver, GUI, desktop session or license is unavailable, supply a reproducible plan and mark execution NOT_RUN.
- **Evidence ladder:** L0 = text/metadata/static checks; L1 = successful project import, native ERC/DRC/rebuild or simulation with logs; L2 = independently observed physical behavior or fabrication inspection when relevant. An L1 solve is not proof of L2 physical validity.
- **Reproducibility:** capture exact project revision, solver/application version, libraries, material properties, dimensions/units, seeds and settings, tool commands, runtime constraints and output paths. Prefer native editable files plus portable exports.
- **Safety:** never trigger fabrication orders, machine motion, destructive edits, paid cloud compute, large solver sweeps or transfer of confidential customer design without explicit approval.
- **Integration:** adapters/MCP servers must be explicitly installed, authenticated/authorized and probed with read-only calls before being treated as available. Skill instructions cannot themselves provide application access.
- **Release quality:** inspect requested metrics, tolerance bands, warning waivers, report dates and artifacts. Distinguish a missing test from a passing one.

## References

- https://www.cadence.com/en_US/home/tools/system-analysis/rf-microwave-design/awr-design-environment-platform.html
- Use the exact installed AWR Automation/Scripting Guide for working examples.

Additional domain-specific checklist: [references/verification.md](references/verification.md).
