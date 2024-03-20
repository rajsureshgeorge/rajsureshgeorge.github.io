## Interrupts in Riscv from the view from a embedded guy
### Interrupt Controllers
There are basically two types of interrupt controllers.

i. SIC (Simple Interrupt Controller)

ii. PLIC (Platform Level Interrupt Controller)

---------
i. SIC (Simple Interrupt Controller)

From the name itself, it is known that it is a simple controller for interrupts. It is a minimal interrupt controller namely for the 32 bit type processors, where priority is based on the interrupts that is received by the controller i.e,. first come first serve
