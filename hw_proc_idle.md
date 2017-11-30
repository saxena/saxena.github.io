# Hardware Techniques

## Halting the Processor Clock

Traditional processors are driven by clocks. The clocks drive the
processor to fetch and decode instructions from memory and dispatch
them to appropriate execution units.

However, there are plenty of occasions when the processor does not
have any tasks to perform. For example, when processor is waiting to
handle key-stokes between user input, or when processor waiting to
receive data over the network.

Processor Instruction sets contain special instructions that cause the
processor to enter a quiet state when executed. Such instructions are
typically named `HALT` or `WFI` (Wait For Interrupt).

These instructions cause the processor to pause execution at the
instruction address. The processor continues to be in this state
unless an interrupt is triggered.

The halt state of requires that the processor maintains any
architected state after the instruction has completed execution. The
clock is not required to maintain this state and can be paused.

Pausing the clock prevents clock transitions from propagating to
execution blocks within the processor and associated sub-system and
minimized any internal state transition to occur.

This helps reduce dynamic power consumption component to 0 and leaves
the processor in a state such that the only power consumed in the
processor is the static leakage power that is required to maintain
logical state in the system.

This technique is also referred to as "Clock Gating". On certain
processors the clock gating occurs outside the processor logic. On
other systems the clock is paused before it can propagate to
individual blocks.

Fine grained gating of the clock can help build functional blocks that
remain functional to carry out book keeping tasks like timer
sub-systems. Such always on timer blocks cause be used to keep system
time or to allow profiling system to count duration for which the
processor was halted.

## Freezing the Processor

Processor often consist of multiple domain of logic and memory.

Cache cells might be optimized for different speed and voltage
settings.

## Powering off the Processor

## Powering off Clocks and underlying PLLs
