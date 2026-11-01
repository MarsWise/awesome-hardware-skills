---
name: kicad-pcb
description: Use for KiCad schematic and PCB projects, kicad-cli electrical rule checks, PCB design rule checks, footprint validation, netlist and BOM outputs, fabrication Gerbers, drill files and manufacturing preflight.
---

# KiCad | Reproducible Schematic & PCB Toolchain

## Use when

Use for KiCad schematic and PCB projects, kicad-cli electrical rule checks, PCB design rule checks, footprint validation, netlist and BOM outputs, fabrication Gerbers, drill files and manufacturing preflight.

## Runtime discovery

- Native tool: `kicad-cli` from an installed KiCad release; check `kicad-cli version`.
- Inputs: `.kicad_pro`, `.kicad_sch`, `.kicad_pcb`, libraries, footprint table, stackup, solder mask and Fab/Edge.Cuts.
- The exact subcommand/options can differ by release. Run `kicad-cli sch erc --help` or `kicad-cli pcb drc --help` before using version-specific flags.

## Working procedure

1. Clone or copy the project. Confirm all hierarchical sheets, libraries, libraries' license, project text variables, stackup, copper layers, net classes and PCB rules are accessible.
2. Run schematic ERC: `kicad-cli sch erc -o reports/erc.rpt design.kicad_sch`. Inspect **reported violations**, not just process exit code; rerun after changes.
3. Run PCB DRC: `kicad-cli pcb drc -o reports/drc.rpt design.kicad_pcb` (verify syntax in installed version). Review unconnected nets, shorts, clearances, mask slivers, hole/via clearances, silkscreen and missing board outline.
4. Review schematic-to-PCB connectivity and footprint pinouts, component orientation, thermal relief, planes, signal-integrity considerations and critical design constraints not modeled by native DRC.
5. After approval, export layer-specific Gerbers using `kicad-cli pcb export gerbers` and inspect the release's drill-export syntax via `--help`. Produce BOM/position outputs as supported.
6. Inspect exported Gerber/drill with an independent viewer or CAM checker; verify stackup, layer map, drill units, X/Y origin, file counts, fiducials and assembled BOM.
7. Return native projects, text reports, manufacturing files and exact version/commands; no fabrication order without explicit confirmation.

## Engineering checks

- ERC and DRC reports generated with the same design revision.
- Warnings/violations reviewed and waived individually, not ignored.
- Gerber/drill origin, units, layer map and outline confirmed.
- BOM, schematic refs and PCB footprints reconciled.

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

- https://docs.kicad.org/9.0/en/cli/cli.html
- https://docs.kicad.org/master/en/cli/cli.html

Additional domain-specific checklist: [references/verification.md](references/verification.md).
