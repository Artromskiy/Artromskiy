# Artromskiy

Most of my public work is one long experiment: how much of a game engine can I build myself in C# and Vulkan, and where do the boundaries between its parts need to be?

The current Delta stack is split into the pieces I actually need:

- [DeltaEngine](https://github.com/Artromskiy/DeltaEngine) — the host, window and frame lifecycle;
- [DeltaRender](https://github.com/Artromskiy/DeltaRender) — a Vulkan render graph for windowed and offscreen work;
- [DeltaECS](https://github.com/Artromskiy/DeltaECS) — archetypes, chunked SoA storage, queries and generated iteration;
- [DeltaMaths](https://github.com/Artromskiy/DeltaMaths) — vectors, matrices and fixed-point math shared by CPU and shader code;
- [DeltaShader](https://github.com/Artromskiy/DeltaShader) — a C# to GLSL/SPIR-V compiler with explicit GPU data packing;
- [DeltaText](https://github.com/Artromskiy/DeltaText) and [DeltaXAML](https://github.com/Artromskiy/DeltaXAML) — text shaping and a renderer-neutral UI layer.

This is not a finished engine or a polished framework. It is the engine being assembled: APIs change, parts are replaced, and the useful result is in the code and the small experiments around it.

## A few things worth opening

### [Sky Pirates](https://github.com/Artromskiy/SkyPirates)

A Unity tactical game prototype I worked on before the Delta stack. The simulation uses fixed ticks and fixed-point math, shares state between client and server, and supports command replay and rollback.

- [Timeline and replay loop](https://github.com/Artromskiy/DVG.SkyPirates.Shared/blob/main/Services/TimelineService.cs)
- [Pooled history storage](https://github.com/Artromskiy/DVG.Core/blob/main/Components/History.cs)
- [Prototype README and demo](https://github.com/Artromskiy/SkyPirates#readme)

### [DeltaShader](https://github.com/Artromskiy/DeltaShader)

The shader side is deliberately written as a compiler: Roslyn checks the supported C# subset, the compiler builds typed IR, and the backend emits GLSL/SPIR-V artifacts. The CPU-side packing code and ABI are tested alongside the compiler.

- [Shader compiler entry point](https://github.com/Artromskiy/DeltaShader/blob/main/src/DeltaShader.Compiler/Frontend/ShaderBodyTranslator.cs)
- [ABI types](https://github.com/Artromskiy/DeltaShader/blob/main/src/DeltaShader.Contract/ShaderAbi.cs)
- [Std430 packing tests](https://github.com/Artromskiy/DeltaShader/blob/main/tests/DeltaShader.Compiler.Tests/Std430PackingTests.cs)

### [DeltaECS](https://github.com/Artromskiy/DeltaECS)

The ECS is an attempt to keep the storage core blind and cheap while giving typed C# code a useful way to iterate it. Query plans are cached, structural work is batched, and generated consumers keep type knowledge at the edge.

- [Storage and query notes](https://github.com/Artromskiy/DeltaECS/blob/main/docs/README.md)
- [Benchmark and JIT-disassembly notes](https://github.com/Artromskiy/DeltaECS/blob/main/docs/benchmarks/README.md)

## What I pay attention to

- data layout, ownership and lifetime before adding another abstraction;
- the actual JIT output and assembly when a hot loop matters;
- generated code for repetitive typed paths, with small contracts between projects;
- deterministic state, rollback and explicit resource transitions.

[Email](mailto:artromskiy@gmail.com) · [Telegram @RumTerry](https://t.me/RumTerry)
