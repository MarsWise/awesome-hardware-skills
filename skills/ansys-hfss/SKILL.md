---
name: ansys-hfss
description: Use for Ansys HFSS 3D RF and antenna simulation, PyAEDT automation, electromagnetic ports and boundaries, adaptive meshing, convergence checks, Touchstone export and independent EM model review.
---

# Ansys HFSS | PyAEDT & Solver Validation

## Use when

Use for Ansys HFSS 3D RF and antenna simulation, PyAEDT automation, electromagnetic ports and boundaries, adaptive meshing, convergence checks, Touchstone export and independent EM model review.

## Runtime discovery

- Native tool: Ansys Electronics Desktop with a licensed HFSS solver; Python package `ansys-aedt-core` (PyAEDT) is an automation client, not a solver.
- Project: `.aedt`, model variables, solution type, frequency sweep, units, port/field configuration.
- Prefer documented PyAEDT API for the installed release; begin with `from ansys.aedt.core import Hfss` after dependency and desktop detection.
- AEDT/solver may require Windows or a supported remote installation; a Codex/WSL/Docker environment alone cannot imply access.

## Working procedure

1. Define solution type (driven modal/terminal, eigenmode, SBR+ or other), frequency band, accuracy targets and licensing constraints.
2. Inspect geometry units, conductor and dielectric properties, mesh operations, coordinate system, boundary assignments, radiation region and port cross-sections.
3. Select excitation correctly (wave, lumped or terminal) and verify polarity, integration lines, conductor association, reference planes and impedance normalization.
4. In a **copy of the design**, create/update analysis using release-matched `Hfss.create_setup`, then define a frequency sweep using the installed PyAEDT APIs. Validate exact API signatures rather than extrapolating examples.
5. Capture the actual solve status, message manager errors, convergence history (Delta-S or relevant metric), mesh statistics and nominal S-parameter results.
6. Re-run at tighter convergence, inspect resonant shifts, modal cutoffs, passivity/energy conservation and field concentration.
7. Export actual Touchstone/CSV/field outputs and script/desktop versions. Compare with CST or measurement only where available; never present a cross-tool comparison that has not run.

## Engineering checks

- Solution type and wave-port modes match the design problem.
- HFSS project has a completed, non-error, converged setup.
- Saved S-parameter files list correct port map and impedance.
- HFSS/CST comparison uses matched units, materials and calibration planes.

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

- https://aedt.docs.pyansys.com/version/stable/API/_autosummary/ansys.aedt.core.hfss.Hfss.create_setup.html
- https://aedt.docs.pyansys.com/version/stable/API/Setup.html

Additional domain-specific checklist: [references/verification.md](references/verification.md).
