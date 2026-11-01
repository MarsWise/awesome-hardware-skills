---
name: altium-designer
description: Use for Altium Designer schematic and PCB design, .PrjPcb projects, .SchDoc and .PcbDoc files, libraries, DelphiScript automation, ERC, DRC, BOM validation and manufacturing release.
---

# Altium Designer | PCB & Schematic Engineering

## Use when

Use for Altium Designer schematic and PCB design, .PrjPcb projects, .SchDoc and .PcbDoc files, libraries, DelphiScript automation, ERC, DRC, BOM validation and manufacturing release.

## Runtime discovery

- Native tool: Altium Designer on an authorized Windows workstation with project access.
- Project inputs: `.PrjPcb`, `.SchDoc`, `.PcbDoc`, `.OutJob`, libraries, variants and board rules.
- Supported approach: native scripting projects (`.PrjScr`) using **DelphiScript** and the installed version's object model. Legacy VBScript/JScript is version/setting dependent; do not assume it is enabled.
- A CLI, API or MCP capability is **not** implied by this skill; first establish the actual installation and tool bridge.

## Working procedure

1. Inventory project hierarchy, sheet connectivity, component models, versions/variants, stackup, board rules and output jobs; identify stale or missing dependencies.
2. Compile/validate the schematic in Altium, run electrical rule checks, and record the actual Messages-panel report. Identify ambiguous power nets, unconnected pins, variant issues and footprint mismatches.
3. Check PCB synchronisation, clearance, minimum width, drill, impedance/stackup, copper return paths, differential pair geometry, length/skew constraints and assembly clearances; run the project's real DRC.
4. Stage any scripts against a **copy**. Limit script edits to explicit query results and retain a before/after change record; inspect available scripting API in that Altium release.
5. Generate deliverables using configured OutputJobs: fabrication files (Gerber/ODB++ as applicable), drill, drawings, BOM, placement and assembly outputs. Check file contents, variants, units and revision consistency.
6. Report every unresolved ERC/DRC issue and waiver; independent CAM/DFM and assembly review are required before manufacturing release.

## Engineering checks

- Input revisions and component-library references resolved.
- Actual schematic/PCB check reports are attached; not inferred.
- Fitted/unfitted BOM, Gerber/ODB++ and drill layer counts independently checked.
- Native project saved, reopened and source/output revision matched.

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

- https://www.altium.com/documentation/altium-designer/scripting
- https://www.altium.com/documentation/altium-designer/scripting/language-support

Additional domain-specific checklist: [references/verification.md](references/verification.md).
