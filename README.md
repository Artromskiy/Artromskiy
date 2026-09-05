# Artromskiy

### Game engine & graphics programmer · C# / .NET

I build the systems behind real-time applications: deterministic simulation, data-oriented storage, shader compilation and GPU rendering. I care about clear data flow, explicit resource ownership and understanding what the generated code actually does.

**Open to game engine / graphics programming roles**, especially rendering, simulation and performance-critical infrastructure.

[Email](mailto:artromskiy@gmail.com) · [Telegram @RumTerry](https://t.me/RumTerry)

## Start with these projects

### [Sky Pirates](https://github.com/Artromskiy/SkyPirates) — deterministic game simulation

A Unity tactical game prototype set on floating islands. The simulation is shared between client and server and separated from presentation.

- Fixed-tick simulation and fixed-point math for deterministic state updates.
- Lockstep networking, command replay and rollback of simulation history.
- ECS-based game logic, with pooled history storage and explicit model/view boundaries.

**Explore:** [Prototype & demo](https://github.com/Artromskiy/SkyPirates#readme) · [Rollback & replay loop](https://github.com/Artromskiy/DVG.SkyPirates.Shared/blob/main/Services/TimelineService.cs) · [Pooled history implementation](https://github.com/Artromskiy/DVG.Core/blob/main/Components/History.cs)

### [DeltaShader](https://github.com/Artromskiy/DeltaShader) — C# → SPIR-V

A shader compiler and authoring toolchain for Vulkan. Supported C# shader code goes through Roslyn validation and a typed intermediate representation to GLSL and SPIR-V.

- Compile-time diagnostics for unsupported constructs and resource usage.
- Explicit shader ABI and generated CPU-to-GPU data packing.
- Compiler, command-line/build tooling and runtime artifacts kept separate.

**Explore:** [Architecture & usage](https://github.com/Artromskiy/DeltaShader/blob/main/docs/README.md) · [Shader translation](https://github.com/Artromskiy/DeltaShader/blob/main/src/DeltaShader.Compiler/Frontend/ShaderBodyTranslator.cs) · [Packing tests](https://github.com/Artromskiy/DeltaShader/blob/main/tests/DeltaShader.Compiler.Tests/Std430PackingTests.cs)

### [DeltaECS](https://github.com/Artromskiy/DeltaECS) — data-oriented .NET runtime

An archetype ECS with chunked structure-of-arrays storage, cached query plans and source-generated iteration.

- Typed component access over a non-generic storage/query core.
- Batched structural operations and reusable query state.
- Benchmark and JIT-disassembly workflows for investigating hot loops.

**Explore:** [Storage & query design](https://github.com/Artromskiy/DeltaECS/blob/main/docs/README.md) · [Benchmark methodology](https://github.com/Artromskiy/DeltaECS/blob/main/docs/benchmarks/README.md)

## More of the Delta stack

These libraries explore the other parts of a C# engine, with explicit contracts between subsystems.

| Project | Focus |
| --- | --- |
| [DeltaRender](https://github.com/Artromskiy/DeltaRender) | Vulkan render graph for raster, compute and transfer workloads; windowed and offscreen execution. |
| [DeltaMaths](https://github.com/Artromskiy/DeltaMaths) | Portable vectors, matrices, swizzles and deterministic fixed-point math. |
| [DeltaXAML](https://github.com/Artromskiy/DeltaXAML) | Retained UI, typed properties/bindings and a renderer-neutral display list. |

## How I approach engineering

- Make memory ownership, data layout and lifecycle visible in the design.
- Measure hot paths with benchmarks and inspect JIT output before claiming an optimization.
- Use code generation for repetitive typed code; keep runtime contracts small and dependencies explicit.

Sky Pirates is a prototype; the Delta libraries are under active development. Each repository documents its scope and licensing.
