---
name: solidworks-cad
description: Use for SOLIDWORKS parametric part and assembly modeling, macros through the documented COM API, configuration-aware drawings, mates, rebuild status, interference review and STEP or native CAD release.
---

# SOLIDWORKS | Parametric Mechanical CAD

## Use when

Use for SOLIDWORKS parametric part and assembly modeling, macros through the documented COM API, configuration-aware drawings, mates, rebuild status, interference review and STEP or native CAD release.

## Runtime discovery

- Native tool: SOLIDWORKS licensed desktop on Windows; inspect edition and API version.
- Inputs: `.SLDPRT`, `.SLDASM`, `.SLDDRW`, external references, configurations, custom properties and material/mass settings.
- Supported API: documented VBA/COM or .NET interop (C#, VB.NET). Inspect installed SOLIDWORKS type libraries and examples; do not guess methods based on unrelated CAD APIs.
- Model modification via macro is distinct from a standalone CAD kernel: an installed active SOLIDWORKS instance or supported automation environment is required.

## Working procedure

1. Inventory assemblies, parts, drawing references, configurations, mates, suppression state, units, feature tree and dependencies. Identify lightweight or unresolved components.
2. Establish baseline: regenerate/rebuild, capture failed features, dangling references, zero-thickness issues and native mass-property summary.
3. Confirm design intent and critical constraints: clearance envelopes, interference, thread fits, tolerance stackups, materials, load paths, manufacturing methods and drawing datum schemes.
4. Generate or update named parametric features in a copied assembly via a **version-tested** SOLIDWORKS macro or documented API, retaining feature IDs/configuration state and a log of changed dimensions.
5. Rebuild all affected configurations; run assembly interference detection and mating consistency checks, not only visual inspection. Check drawing views, dimensions, BOM balloons and title-block revisions.
6. Export STEP/Parasolid/STL as appropriate. Reimport to a clean document when feasible; compare body counts, bounding boxes, units, assembly transforms and mass-property changes.
7. Stop before machine operations, CAM toolpath postprocessing or procurement until user approval and proper mechanical signoff.

## Engineering checks

- No unresolved/dangling external references in released assembly.
- Rebuild errors and mate violations enumerated explicitly.
- Interference and assembly clearance checked for relevant configurations.
- Exported geometry independently reopened and units verified.

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

- https://help.solidworks.com/2026/english/api/sldworksapiprogguide/Welcome.htm
- https://help.solidworks.com/2026/english/SolidWorks/sldworks/c_solidworks_api.htm

Additional domain-specific checklist: [references/verification.md](references/verification.md).
