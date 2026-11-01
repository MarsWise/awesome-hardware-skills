---
name: keysight-systemvue
description: Use for Keysight SystemVue RF and DSP communication-system models, waveform generation, EVM/BER/ACLR studies, phased-array impairments, Python-based design automation, simulator datasets and MCP integration where licensed.
---

# Keysight SystemVue | RF/DSP System Engineering

## Use when

Use for Keysight SystemVue RF and DSP communication-system models, waveform generation, EVM/BER/ACLR studies, phased-array impairments, Python-based design automation, simulator datasets and MCP integration where licensed.

## Runtime discovery

- Native application: licensed Keysight SystemVue; identify installed build and libraries.
- In **SystemVue 2026 Update 1**, Keysight documents integrated MCP and Python APIs. An earlier build may lack them.
- Starting the SystemVue MCP server requires a SystemVue Core Platform license; specific analysis libraries and simulation engines may need additional licenses.
- Treat workspace/session access as untrusted until connection, version, license and one read-only tool discovery are verified.

## Working procedure

1. Identify signal chain, RF band, sampling rate, interpolation, noise bandwidth, modulation, coded throughput, input power and system targets.
2. Read model workspace and dataset versions. Trace source, pulse shaping, impairments, PA/LO, channel, RF_Link, ADC/DAC and receiver correction blocks.
3. Establish baseline with fixed random seed and documented simulation length. Record actual EVM, BER/PER with confidence, ACLR, spectral masks, timing and processing gain as relevant.
4. Use documented **installed** Python/MCP APIs to inspect components, change one parameter at a time, run licensed simulations and export their real results. Do not invent endpoints, magic method names or numeric improvements.
5. Sweep quantization, LO phase noise, PAPR/backoff, adjacent interference, PA compression, thermal variation and antenna pointing only where model blocks support them.
6. Compare waveform, power, EVM and BER against executable Python/MATLAB reference or a measured instrument capture when available; mark any unmatched models as assumptions.
7. Save workspace plus settings/results and a reproducible report with parameter table and explicit PASS/FAIL/NOT_RUN.

## Engineering checks

- Measured vs simulated metrics explicitly distinguished.
- Seeds, simulation length, SNR definition, EVM reference and waveform units recorded.
- Required simulator and library licenses verified.
- Frequency-domain power and noise reference conventions documented.

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

- https://www.keysight.com/us/en/lib/resources/software-releases/system-design-systemvue-2026-update-1.html
- Review the installed SystemVue Python API reference, MCP guide and release notes.

Additional domain-specific checklist: [references/verification.md](references/verification.md).
