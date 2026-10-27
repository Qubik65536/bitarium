# Bitarium

**A playground for experimenting with computer architecture, CPU emulation, virtual hardware, and low-level tooling.**

The first machine is a RISC-V RV32I computer emulated at the instruction level, with precise traps and configurable RAM. It runs assembly programs that can be run to completion or stepped through and inspected in a terminal UI, and every result can be cross-checked against an independent reference model.

- **Rust** — instruction decoding and execution, machine composition and program loading, the command-line application, and an optional debugger with breakpoints, traces, and register and memory panels.
- **Zig** — native memory and virtual devices with checked bounds, alignment, and permissions, linked into the Rust side as a static library through a narrow C-compatible interface.
- **OCaml** — the assembler (labels, checked operands, raw binaries with separate symbol files), the disassembler, and an independent reference interpreter whose results are compared against the emulator.

Bitarium runs on Linux and macOS (x86_64 and ARM64). Its components sit behind explicit interfaces, leaving room for other ISAs, configurable machine descriptions, richer devices, and timing models.

## Runtime and Assembly Subsystems

| Directory | Description |
| --- | --- |
| `subsystem/cpu/` | Rust-based CPU model covering registers, instruction decoding and execution, and architectural traps. |
| `subsystem/memory/` | Zig-based RAM and ROM memory models and memory I/O services with bounds and permission checks. |
| `subsystem/devices/` | Zig-based virtual device models and device I/O services, including memory/device access routing. |
| `subsystem/machine/` | Rust-based machine system composing CPU, memory, and devices, with stepping, running, and inspection. |
| `subsystem/assembler/` | OCaml-based assembler library and command-line toolchain front end. |

## Development and Inspection Tools

| Directory | Intended Contents |
| --- | --- |
| `tooling/debugger/` | Rust-based debugging system with breakpoints, stepping, pause and continue, inspection, and traces. |
| `tooling/disassembler/` | OCaml-based disassembler library and command-line tool that turns instruction bytes into readable assembly. |
| `tooling/reference-model/` | Simple, independent OCaml RV32I interpreter for cross-checking the Rust CPU model. |
| `tooling/verification/` | Comparison harnesses, proof experiments, and verification utilities. |
| `tooling/build/` | Build system and test orchestration helpers. |

## Application, Programs, and Documentation

| Directory | Intended Contents |
| --- | --- |
| `app/` | Rust command-line application and terminal UI that configures, loads, runs, and debugs the machine. |
| `programs/` | Guest assembly examples and test programs with known expected results. |
| `docs/architecture/` | Architecture documentation of component design, the machine model and rules, interfaces, and decision rationale. |
| `docs/usage/` | Usage documentation of installation, application commands, debugger controls, and examples. |
| `docs/development/` | Development documentation of building, testing, debugging the host software, and contributor workflow. |
