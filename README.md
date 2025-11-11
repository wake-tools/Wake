# [Wake](https://github.com/wake-tools/Wake-Lang) JIT Engine

> The live JIT runtime powering **[Wake Lang](https://github.com/wake-tools/Wake-Lang)**.

### What is Wake?
Wake is a small, embeddable JIT runtime that executes C99 code and **Wake Lang** scripts 

### Key Features
-  **Live JIT** — live feedback
-  **Integrated Debugger** — see everything, fix anything
-  **Safe Memory** —  bound checking and runtime safety
-  **Wake Lang Integration** — lightweight linear scripting layer
-  **Flexible Packages** — signed .wpkg modules with strict dependency resolution
-  **Multi-Platform** — Windows (w32/w64), (macOS soon)

## Typical Wake Structure
```bash
cd wake
```
```c
env/              // Environement Specific Launcher System
├──wake-w32-d       // use system windows 32-bit in debug type mode
└──wake-w64-r       // use system windows 64-bit in release type mode

runtime/          // Cache Runtime Binaries (extracted from packages)
├──include/         // external library headers
├──libs/            // static or dynamic libraries (*.dll, *.def, *.so, *.dylib, ...)
└──modules/         // backend tools (TCC, sokol-shdc, ...)

package/          // list of pre-loaded or fetched packages which are compressed & encrypted (*.wpkg)

wake              // default system launcher (one of those from env/)
wk-w32              // wake runtime 32-bit
wk-w64              // wake runtime 64-bit
```
> `runtime` folder can be rebuilt at anytime from the packages
---

## Typical JIT Process Runtime
```bash
wake app.jc
```
```csharp
[Process] Wake > app.jc [Master Orchestrator & Main Runtime] (creates the console)            
|    |
|    [Parse app.jc] (C source code + metadata header)         <------------------|
|    |                                                                           |
|    [Parse metadata] <:jit:> Wake-Lang metadata <:/jit:> (build instructions)   |
|    |                                                                           |
|    [Process] TCC (Compiler) -xc shared app.jc -o out.sm                        |
|    |                                                                           |
|    [Process] GDB (Debugger)                                                    |
|        |                                                                       |
|        [Process] Wake > out.sm [Recursive Instance] (In-Memory PE Loader)      |
|            |                                                                   |
|            [Link] link libraries & bound checking (PE link functions)          |
|            |                                                                   |
|            [Launch] main                                                       |
|                |                                                               |
|                |--> In-code jitlib: launch Wake-Lang sub-JIT -- (recursive) -->|
|                                                                                |
|                                                                                |
|--> [Check for file modification] --> (if true) --> Send reload signal -------->|
```

---
## [|>](https://github.com/wake-tools/Wake-Lang) {Wake-Lang}


> ### Quick start (Hello)
```bash
wake hello.jc
```

```c
/*|------------------------------------------------------------>>
  | wake hello.jc
  |------------------------------------------------------------>>
    <:jit:w32|w64>
        {wk.module.sys.r}wake-tools/tcc-v0.1w/tcc
            -xc -shared {this.file}
            -o hello.sm
    <:/jit:>
  |------------------------------------------------------------>>
*/
#include <stdio.h>

int main(void) {
    printf("Hello, Wake!\n");
    return 0;
}

```
> **Wake up. Build boldly. JIT Awaken.**

---
##  Get Started

## goto > **[samples](https://github.com/wake-tools/Wake-Samples)**

A small set of **JIT C (.jc)** examples that run instantly with Wake: edit, save, it reloads.  
> No build system. No project setup. Just code → run.

**What you’ll see**
- Graphics with Sokol and Dear ImGui (pure C bindings)
- Live reload while editing
- Runtime safety with bound checking
- A minimal, portable structure per sample
---
## goto > **[wake.tools](https://wake.tools)** 
>
> Official website, download the latest build, explore live demos, and follow development updates.
---
