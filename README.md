# Bitarium

**A playground for experimenting with computer architecture, CPU emulation, virtual hardware, and low-level software.**

The first machine targets RISC-V RV32I. Rust implements CPU execution and the application; Zig implements native memory and devices; OCaml implements assembly tools and an independent reference model.

## Runtime and Assembly Subsystems

| Directory | Intended Contents |
| --- | --- |
| `subsystem/cpu/` | Rust-based CPU state and instruction execution. |
| `subsystem/memory/` | Zig-based RAM and ROM memory models and memory I/O services. |
| `subsystem/devices/` | Zig-based virtual devices and device I/O services. |
| `subsystem/machine/` | Rust-based composition of CPU, memory, and devices into a complete machine. |
| `subsystem/assembler/` | OCaml-based assembler library and command-line tool. |

## Development and Inspection Tools

| Directory | Intended Contents |
| --- | --- |
| `tooling/debugger/` | Rust-based machine debugger (execution controls, breakpoints, and inspection) library and command-line interface. |
| `tooling/disassembler/` | OCaml-based disassembler library and command-line tool. |
| `tooling/reference-model/` | Simple OCaml RV32I implementation for cross-checking the Rust CPU implementation. |
| `tooling/verification/` | Proof experiments and verification harnesses. |
| `tooling/build/` | Build and test orchestration utilities. |

## Application, Programs, and Documentation

| Directory | Intended Contents |
| --- | --- |
| `app/` | Rust command-line application and terminal UI for running and debugging the machine. |
| `programs/` | Guest assembly examples. |
| `docs/architecture/` | Component design, machine specification, interfaces, and decision rationale. |
| `docs/usage/` | Installation, application commands, debugger controls, and examples. |
| `docs/development/` | Building, testing, debugging the host software, and contributor workflow. |
