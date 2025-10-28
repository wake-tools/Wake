# [Wake](https://github.com/wake-tools/Wake-Lang) JIT Engine

> The live JIT runtime powering **[Wake Lang](https://github.com/wake-tools/Wake-Lang)**.

### What is Wake?
Wake is a small, embeddable JIT runtime that executes C99 code and **Wake Lang (.jc)** scripts with zero build time.

### Key Features
-  **Live JIT** — live feedback
-  **Integrated Debugger** — see everything, fix anything
-  **Safe Memory** —  bound checking and runtime safety
-  **Branchless & Deterministic** — linear, predictable execution flow
-  **Wake Lang Integration** — lightweight scripting layer for automation and prototyping
-  **Flexible Packages** — signed .wpkg modules with strict dependency resolution
-  **Multi-Platform** — Windows (w32/w64), (macOS soon)

## Typical JIT App Architecture
```bash
wake > app.jc
```
```csharp
[Process] Wake (Master Orchestrator - Main Runtime) (creates the console)            
|    |
|    [Reads app.jc] (C source code + metadata header)         <------------------|
|    |                                                                           |
|    <:jit:> Wake-Lang metadata <:/jit:> (compile & link instructions)           |
|    |                                                                           |
|    [Process] TCC -xc -shared out.sm                                            |
|    |                                                                           |
|    [Process] GDB (Debugger)                                                    |
|        |                                                                       |
|        [Process] wake (In-Memory PE Loader)(parsing sections .text, .data ..)  |
|            |                                                                   |
|            [Link] link libraries & bound checking                              |
|            |                                                                   |
|            [Launch] main                                                       |
|                |                                                               |
|                |---- (Jitlib -> launch sub-JIT < Wake-Lang >)  ----------------|
|                                                                                |
|                                                                                |
| [Check for file modification] --> (if true) --> Send reload signal ------------|
```

---
## [|>](https://github.com/wake-tools/Wake-Lang) {Wake-Lang}


> ### Quick start (Hello)
```bash
wake > hello.jc
```

```c
/*|------------------------------------------------------------>>
  | wake > hello.jc
  |------------------------------------------------------------>>
    <:jit:w32|w64>
        {wk.module.sys.r}wake-tools/tcc-v0.1w/tcc
            -xc -shared {this.file}
            -o hello.sm
        >
        #Jit.reload
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
## Setup (Early Access)

###  Get Started

> **Early Access Required**  
> Wake is currently in **closed early access**.  
> To download the runtime, please register first at:  
> [Register](https://wake.tools/register.html)  
>

---

## Wake comes in two flavors


### Installer Version (All-in-One Setup)

Perfect for a complete offline install.
Just run the .msi, select your preferred packages, and you’re ready to go.

- Everything is pre-configured
- Works entirely offline
- Instantly runs .jc files from File Explorer

> Ideal if you want the full Wake environment, pre-bundled and ready out of the box.

---

### Portable Version (Minimal & Flexible)

A super-light Wake build that you can copy, move, or duplicate anywhere.
It includes only the essentials, and automatically pulls missing packages when needed.


```bash
# Go to your Wake directory
cd wake

# Register file associations and add Wake to PATH
wake --install

# JIT your first program
wake myapp.jc

# Wake will automatically fetch required packages

### Official Site
- **[wake.tools](https://wake.tools)** — download the latest build, explore live demos, and follow development updates.
```
---
## > **[wake.tools](https://wake.tools)** 
>
> Official website, download the latest build, explore live demos, and follow development updates.
---
