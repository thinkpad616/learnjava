# JVM Internals and Performance (Study Guide + Examples)

## Contents
- Class Loaders (Bootstrap, Platform, Application; parent delegation)
- Verification, Preparation, Resolution, Initialization
- Runtime Data Areas (Heap, Stacks, Method Area, PC, Native)
- Execution Engine (Interpreter, C1/C2 JIT)
- GC Algorithms (Serial, Parallel, G1, ZGC, Shenandoah)
- Object layout and headers (Mark Word), TLABs
- Escape analysis and scalar replacement
- Synchronization optimizations
- JIT optimizations (inlining, on-stack replacement)
- Monitoring and Profiling (JFR, jcmd, jmap, jstack, jstat)
- Startup performance, class data sharing

---

## Class Loading
Parent delegation model prevents multiple definitions of core classes. Custom class loaders can isolate modules/plugins.

## Runtime Data Areas
- Heap for objects; young and old generations.
- Stacks hold frames with local vars and operand stack.
- Method area stores class metadata.

## GC Overview
- G1: region-based, predictable pauses.
- ZGC/Shenandoah: low-latency collectors with concurrent relocation.

## Escape Analysis
If an object does not escape a method/thread, JIT can allocate it on stack (scalar replacement), reducing GC pressure.

## Tools
- JFR (Java Flight Recorder) for low-overhead profiling.
- jcmd, jstack (thread dumps), jmap (heap), jstat (GC stats).
