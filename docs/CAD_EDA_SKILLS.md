# CAD/EDA Skills for Claude Code, Codex, OpenCode and DeepTutor

This directory contains eight **portable Agent Skills** contributed directly to the repository. They guide engineering agents but do **not** bundle proprietary applications, proprietary solvers, licenses or MCP servers.

| Skill | Native engineering target | Principal automation / validation |
|---|---|---|
| `altium-designer` | Altium schematic and PCB | DelphiScript, project compile, ERC/DRC, OutputJobs |
| `cst-studio-suite` | 3D EM, antennas, microwave | Authorized CST automation, mesh convergence, S-parameters |
| `ansys-hfss` | 3D RF / antennas | PyAEDT, adaptive solve checks, Touchstone |
| `keysight-systemvue` | RF/DSP communication systems | Licensed Python/MCP when available, EVM/BER/ACLR studies |
| `cadence-awr` | Microwave Office / RF circuits | AWR release-matched scripting, linear/nonlinear and EM checks |
| `kicad-pcb` | Open schematic and PCB | `kicad-cli` ERC/DRC, BOM, Gerber/drill release |
| `solidworks-cad` | Parametric mechanical CAD | SOLIDWORKS COM/VBA/.NET API, rebuild and mate checks |
| `freecad-cad` | Open parametric CAD | Native FreeCAD Python/macro, shape validation and STEP |

## Install

With a local checkout, copy selected skill **directories**, not only the SKILL.md files, to a host supported location:

- Claude Code: `~/.claude/skills/<skill-name>/SKILL.md`
- Codex: `~/.agents/skills/<skill-name>/SKILL.md`
- OpenCode: `~/.config/opencode/skills/<skill-name>/SKILL.md`
- DeepTutor: place adapted skills inside the configured workspace `skills` directory and confirm recognition in the web UI. A plain copy is not a guarantee that current DeepTutor metadata or activation rules match its schema.

Claude Code can also load the `cad-eda-toolchains` plugin from this repository's `.claude-plugin/marketplace.json` after the marketplace is registered.

## Verification policy

All eight skills are **documentation-level contributions**. No vendor applications or licensed solvers were run during their creation; no L0/L1/L2 benchmark badge is claimed. Before using a workflow, discover the exact installed product version and confirm documented automation interfaces.

- Commercial EDA/CAD products are runtime dependencies only when the user expressly authorizes **their own local engineering workflow**. If integrating a separate vendor-independent web service, keep commercial applications in development/reference validation only, never as a required production computation backend.
- Save design files and solver logs, redact confidential information, and verify licensed use before publishing artifacts.
- Many reference materials target vendor versions that change; use the installed version's documentation in preference to examples.
