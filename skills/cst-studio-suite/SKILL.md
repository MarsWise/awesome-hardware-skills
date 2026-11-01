---
name: cst-studio-suite
description: Use for SIMULIA CST Studio Suite electromagnetic modeling, microwave and sub-THz waveguides, horn and phased-array antennas, RF coupling, S-parameter sweeps, meshing and licensed solver automation.
---

# CST Studio Suite | Electromagnetic Modeling

## Use when

Use for SIMULIA CST Studio Suite electromagnetic modeling, microwave and sub-THz waveguides, horn and phased-array antennas, RF coupling, S-parameter sweeps, meshing and licensed solver automation.

## Runtime discovery

- Native solver: SIMULIA CST Studio Suite, license required; do not substitute Python libraries for CST solvers.
- Inputs: geometry and parameters, exact units, band, materials and loss models, ports, boundaries, mesh settings, convergence targets.
- Interfaces: CST release-dependent automation and macro history, commonly VBA and vendor Python interfaces such as `cst.interface` and `cst.results`. **Probe installed modules and APIs first**; imports differ across releases.
- Use CST solely as a permitted local reference/validation engine when a separate service must run on independent open solvers.

## Working procedure

1. State the EM question and pass/fail targets: frequency range, S11/S21/isolation, gain, efficiency, radiation pattern, field hot spots and tolerances.
2. Audit CAD and mesh geometry: material assignment, conductor thickness and losses, air volumes, overlaps/gaps, mesh transitions, and coordinate units.
3. Select a licensed solver appropriate to physics and bandwidth. Set boundary conditions, symmetry, frequency sampling, adaptive mesh and convergence tolerance explicitly.
4. Configure ports and modes; inspect orientation, calibration/de-embedding plane, impedance, mode count and map of port numbers to actual connectors.
5. Run one small baseline only after the user approves computational expense. Export **actual** solver log, mesh convergence and Touchstone S-parameters.
6. Compare a denser-mesh rerun or independent method where feasible. Inspect passivity, reciprocity where applicable, energy balance, consistency of far-field monitors and sensitivity to material tolerances.
7. Export native project, parameter snapshot, field plots and unmodified result data; flag unavailable solve licenses and missing convergence as NOT_RUN or FAIL.

## Engineering checks

- Port reference planes and reference impedances documented.
- Mesh-convergence evidence on the target observable is present.
- S-parameters and field exports correspond to same solver run and settings.
- No claim of physical antenna measurement without actual instrument data.

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

- https://www.3ds.com/products/simulia/cst-studio-suite
- Consult the Help / Automation and Python API manual installed with the precise licensed release.

Additional domain-specific checklist: [references/verification.md](references/verification.md).
