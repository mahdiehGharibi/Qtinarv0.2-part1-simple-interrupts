# Qtinar OS v0.2 — Simple Interrupts

Qtinar OS v0.2 is a small educational operating system kernel written from scratch in C and Assembly. This version focuses on building a correct and stable interrupt system, including GDT, IDT, PIC remapping, and a working keyboard interrupt. It is designed as a learning project to understand how low‑level OS components interact with hardware on x86 systems.



## ✨ Features in This Version

### Core System Setup
- Multiboot‑compatible kernel (boots with GRUB)
- Global Descriptor Table (GDT) with:
  - Null descriptor
  - Kernel code segment
  - Kernel data segment
- GDT flush implemented in assembly

### Interrupt System
- Interrupt Descriptor Table (IDT) with 256 entries
- 32 CPU exception stubs (ISR0–ISR31)
- PIC remapping from IRQ0–IRQ15 → interrupt vectors 0x20–0x2F
- IRQ1 (keyboard interrupt) fully working
- End‑of‑Interrupt (EOI) handling for PIC

### Keyboard Input
- Basic keyboard interrupt handler
- Prints `"key"` on each keypress (ASCII driver coming in next version)

### VGA Text Output
- Simple VGA text mode driver
- Supports clearing the screen and printing characters/strings

### Build System
- Compiles with `gcc -m32`
- Linked with a custom linker script
- Bootable ISO generated using GRUB (`grub-mkrescue`)
- Runs on QEMU



## 📁 Project Structure
\\\(
Qtinarv0.2-part1-simple-interrupts/
│
├── src/
│   ├── boot.s              # Multiboot entry
│   ├── gdt.c / gdt_flush.s # GDT setup
│   ├── idt.c               # IDT setup
│   ├── interrupts.s        # ISR/IRQ stubs
│   ├── isr.c               # CPU exception handler
│   ├── pic.c               # PIC remapping + masking
│   ├── keyboard.c          # IRQ1 handler
│   ├── vga.c               # VGA text output
│   └── kernel.c            # Kernel entry point
│
├── include/                # Header files
│
├── iso/
│   └── boot/
│       └── grub/
│           └── grub.cfg    # GRUB boot menu
│
├── linker.ld               # Linker script
└── README.md               # This file
)\\\

