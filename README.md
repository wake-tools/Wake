# [Wake](https://github.com/wake-tools/Wake) JIT Engine

> The zero-build, live JIT runtime powering **[Wake Lang](https://github.com/wake-tools/Wake-Lang)**.

### What is Wake?
Wake is a small, embeddable JIT runtime that executes C99 code and **Wake Lang (.jc)** scripts with zero build time.

### Key Features
-  **Live JIT** — live feedback
-  **Integrated Debugger** — in memory debugger
-  **Safe Memory** —  bound checking and runtime safety  
-  **Branchless & Deterministic** — linear, predictable execution flow  
-  **Wake Lang Integration** — lightweight scripting layer for automation and prototyping  
-  **Secure Packages** — signed `.wpkg` modules auto-fetched and verified  
-  **Multi-Platform** — Windows (w32/w64), (macOS soon)  


### Official Site
- **[wake.tools](https://wake.tools)** — download the latest build, explore live demos, and follow development updates.

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
        #Jit.add hello
        >
        {wk.module.sys.r}wake-tools/tcc-v0.1w/tcc
            -xc -shared {this.file}
            -o {jit.file}
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
> [wake.tools/register/register.html](https://wake.tools/register/register.html)  
>

---

### Wake comes in two flavors, depending on how you like to work:

---

## Installer Version — All-in-One Setup

Perfect for a complete offline install.
Just run the .msi, select your preferred packages, and you’re ready to go.

- Everything is pre-configured
- Works entirely offline
- Instantly runs .jc files from File Explorer

Ideal if you want the full Wake environment, pre-bundled and ready out of the box.

---

## Portable Version — Minimal & Flexible

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


