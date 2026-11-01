---
name: freecad-cad
description: Use for FreeCAD parametric 3D mechanical design, Python console and macros, FreeCADCmd or version-specific headless automation, PartDesign features, constraints, shape validity and STEP exports.
---

# FreeCAD | Python-driven Mechanical CAD

## Use when

Use for FreeCAD parametric 3D mechanical design, Python console and macros, FreeCADCmd or version-specific headless automation, PartDesign features, constraints, shape validity and STEP exports.

## Runtime discovery

- Native application: installed FreeCAD. Discover version, GUI console and available command-line executable; some distributions use `FreeCADCmd`, others a version-specific name.
- Python API runs inside FreeCAD's Python environment or a correctly configured external interpreter. A generic system `python -c 'import FreeCAD'` may fail and is not sufficient to judge the installation.
- Inputs: `.FCStd`, linked documents, sketches, custom scripts/macros, materials and assembly conventions.

## Working procedure

1. Inspect model units, constraints, datum planes, feature tree, attachments, expression links, external references and recompute warnings; work on a copy.
2. Prefer parametrically constrained sketches, named features and reusable expressions to opaque imported meshes or hardcoded BRep modifications.
3. Implement a small verified Python macro, run in the installed FreeCAD interpreter, call `doc.recompute()` after relevant edits, and save a native `.FCStd` artifact.
4. Check feature status and shape integrity where available (null shapes, `isValid()`, solids count, closed shells, volume, bounding boxes), and ensure sketches meet intended constraint rules.
5. Export STEP for manufacturing or CAD exchange; reopen the exported model and compare bounding box, volume, topology counts and units.
6. For FEM, confirm solver installation, load cases, mesh convergence and boundary conditions rather than inferring structural safety from a shape-only model.
7. Return macro, native model, STEP, log and comparison table. Never call physical assembly or fabrication validated without downstream inspection.

## Engineering checks

- Script ran under the versioned FreeCAD interpreter.
- Recomputed feature tree has no unexplained errors.
- Solid topology and sketch constraints inspected.
- STEP export round-trip validated with explicit tolerances.

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

- https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Python_scripting_tutorial.md
- https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Scripted_objects.md
- https://www.freecad.org/api/

Additional domain-specific checklist: [references/verification.md](references/verification.md).
