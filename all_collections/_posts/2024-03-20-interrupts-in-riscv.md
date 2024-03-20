## Interrupts in Riscv from the view from a embedded guy
### Interrupt Controllers

---------
There are basically two types of interrupt controllers.

i. SIC (Simple Interrupt Controller)

From the name itself, it is known that it is a simple controller for interrupts. It is a minimal interrupt controller namely for the 32 bit type processors, where priority is based on the interrupts that is received by the controller i.e,. first come first serve.

There only limited controls for the SIC: Enable, Status, Control registers.

ii. PLIC (Platform Level Interrupt Controller)

This is an advanced controller for interrupts i.e,. this can priortize control and limit how an external, software or mtime interrupts be executed. This controller has priority, threshold registers and also has supervisor mode, user mode, machine mode, edge and level controls.

--------

### Different Types of Interrupt

Three Different types of interrupts are:

i. Internal Timer Interrupts (mtime,mtimecmp) : This uses `mtie` bit of mstatus register.

ii. Software Interrupts : This uses `msie` bit of mstatus register.

iii. External Interrupts : This uses `meie` bit of mstatus register.

> If you are checking for external interrupt then `meie` and `mie` bit should be `high` to inform the processor that it must be ready for interrupt.
> Then provide address of Plic Handler to `mtvec` in mstatus register.
> If an external interrupt comes, then it goes to handler function.

