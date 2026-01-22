# x86-Worm-Simulation
In this project, a console based simulation is created in x86 Assembly language (MASM). It offers a visual and statistical examination of infection rates and times of execution.

# Technical Implementation Details.
- Development Environment Assembler: MASM32 (Microsoft Macro Assembler)
- Linker: Microsoft Incremental Linker. Libraries Used:
- kernel32.lib: system functions (Process control, Console I/O, Sleep, Timing).
- user32.lib: This library is used in certain user-interface formatting functions such as wsprintfA.
- Directives: .386 (32-bit instruction set), .model flat, stdcall (Standard Windows calling convention).
  
# Simulation Choice 1: Simple Worm (Sequential).
- Logic: This algorithm uses a Linear Scan (O(n)).
- Mechanism: The code sets a loop counter (ECX) ranging between 0 and 15. It verifies the address of the memory [ESI + ECX]. When the block is 0 (Clean), it is marked 1 (Infect), and waits 50ms to replicate network latency, and then shifts to ECX + 1.
# Simulation Choice 2: Fast Worm (Exponential).
- Logic: This simulates either a recursive or multi-threaded spread.
- Mechanism: The initial index of the simulation is 0 infected. The scan fast loop identifies any infected node at any given time. Once an infected node is discovered it tries to infect its immediate neighbors (Index - 1 and Index + 1) at the same time.
# Simulation Choice 3: Stealth Hack.
- Logic: Relies on modular arithmetic to evade detection.
- Mechanism: The loop runs through the memory but repeats instruction test ecx, 1. This is a bitwise operation that determines whether the address is an odd or even address. The jnz (Jump if Not Zero) instruction jumps all odd addresses.
# Simulation Choice 4: Random Chaos (Linear Congruential Generator)
- Logic: Uses pseudo-random number generator (PRNG) to select targets randomly.
- Mechanism: The code sets a loop counter (ECX) ranging between 0 and 15. It verifies the address of the memory [ESI + ECX]. When the block is 0 (Clean), it is marked 1 (Infect), and waits 50ms to replicate network latency, and then shifts to ECX + 1. 
