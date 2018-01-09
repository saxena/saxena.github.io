---
layout: default
title: Power Management Techniques for Energy Efficient Computer Systems
---

These notes describe techniques used to design and implement Energy
Efficient Computer Systems. Energy Efficient design requires
coordinated use of design technqiues at all levels of the Software and
Hardware and SoC stack.

These techniques form the underlying basis for constructing highly
energy efficient systems. The evolution of these technqiues has been
shaped by the Performance and Power requiremetns for Mobile Smartphone
Platforms. However, as energy efficiency starts to become a dominant
cost determiner for data-center class platforms, we will continue ot
see these technqiues take the next leap for that realm.

## [Introduction]
- Performance, In Context
- Hardware and Software views of a Processor
- Energy Consumption in Digital VLSI Curcuits

## Energy Efficiency at the Pocessor Level

### Energy Efficiency when the Processor is Idle
- [Hardware Techniques]
 - Halting the Processor
 - Freezing the Processor
 - Powering of the Processor
 - Powering Off Clocks and underlying PLLs
 - [Common HW Latencies]
- Software Design
 - The Idle Thread
  - Selecting a low-power mode
  - Transitioning to a low-power mode

### Energy Efficiency when the Processor is Active
- Processor Utilization
- How do you calculate Power Consumtion?
- Dynamic Voltage and Frequency Scaling
- Static Voltage Scaling
 - Continous Static Voltage Scaling
  - Silicon, Temperature and Aging

## Energy Efficiency at the SoC Level
- Coordinating Low-Power Modes across Processors in a SoC
- Achieving Low-Power Modes for shared System Resources like System
  Buses, Clocks and Power Supplies

## Energy Efficiency for Multi-processors
- Performance and Energy Aware Thread Scheduling

[Introduction]: chapter_introduction
[Hardware Techniques]: hw_proc_idle
[Common HW Latencies]: hw_proc_latency
