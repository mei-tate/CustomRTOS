# CustomRTOS

A lightweight, priority-based Real-Time Operating System (RTOS) developed from scratch for ARM Cortex-M microcontrollers. The project explores the fundamental concepts of real-time operating system design, including task scheduling, context switching, task management, and interrupt handling.

The initial implementation targets the **STM32F446RE** microcontroller and its ARM Cortex-M4 processor.

## Table of Contents

- [Overview](#overview)
- [Development Board](#development-board)
- [Features](#features)
- [Architecture](#architecture)
  - [System Overview](#system-overview)
  - [Task Management](#task-management)
  - [Scheduling](#scheduling)
  - [Context Switching](#context-switching)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Building and Running](#building-and-running)
  - [Configuration](#configuration)
- [Code Example](#code-example)
- [API Reference](#api-reference)
- [Project Structure](#project-structure)
- [Development Roadmap](#development-roadmap)
- [References](#references)

---

## Overview

CustomRTOS is an educational and experimental project focused on understanding and implementing the core components of a real-time operating system without relying on an existing RTOS kernel.

The primary goal is to develop a functional RTOS with priority-based task scheduling while exploring low-level hardware interactions and ARM Cortex-M architecture.

The project is intended to provide a practical understanding of:

- Real-time scheduling algorithms
- Task creation and management
- CPU context switching
- Hardware interrupts and exceptions
- Stack management
- Embedded systems programming

## Development Board

The initial implementation is designed for the **STMicroelectronics NUCLEO-F446RE** development board, featuring the STM32F446RET6 microcontroller.

<Insert image of NUCLEO-F446RE development board here>

| Component | Specification |
|---|---|
| Development Board | NUCLEO-F446RE |
| Microcontroller | STM32F446RET6 |
| Processor Core | ARM Cortex-M4 |
| Architecture | ARMv7E-M |
| FPU | Single-precision hardware FPU |
| Maximum CPU Frequency | 180 MHz |
| Flash Memory | 512 KB |
| SRAM | 128 KB |

The STM32F446RE provides the hardware resources needed to explore embedded RTOS development, including hardware timers, nested interrupts, and processor exception handling.

## Features

The following list distinguishes between implemented functionality and planned features as development progresses.

### Planned Core Features

- [ ] Priority-based task scheduling
- [ ] Task creation and management
- [ ] Task state management
- [ ] Preemptive multitasking
- [ ] CPU context switching
- [ ] System tick timer
- [ ] Stack allocation and management
- [ ] Idle task
- [ ] Critical section management
- [ ] Interrupt and exception handling
- [ ] Inter-task communication and synchronization

## Architecture

CustomRTOS is designed around a modular kernel architecture. The kernel will manage task execution, scheduling, processor context, and hardware interactions.

### System Overview

<Insert RTOS architecture diagram here>

The main components of the RTOS are expected to include:

| Component | Responsibility |
|---|---|
| Kernel | Coordinates core RTOS functionality |
| Scheduler | Determines which task executes next |
| Task Manager | Creates and manages task control structures |
| Context Switcher | Saves and restores processor context |
| System Timer | Generates periodic interrupts for scheduling |
| Hardware Abstraction | Provides access to MCU-specific peripherals |

### Task Management

Each task will have its own execution context and stack. Task control information will be maintained through a Task Control Block (TCB).

The TCB is expected to contain information such as:

- Task priority
- Task state
- Stack pointer
- Stack information
- Task identifier

### Scheduling

The kernel will use priority-based scheduling to determine which task receives CPU execution time.

Higher-priority tasks will take precedence over lower-priority tasks. The scheduler will determine when task switches are necessary based on task readiness, priority, and scheduling events.

### Context Switching

Context switching allows the processor to transition between tasks while preserving their execution states.

The implementation will explore ARM Cortex-M exception handling and processor registers to save and restore task contexts.

## Getting Started

### Prerequisites

The following tools are required to build and run the project:

- ARM GCC toolchain (`arm-none-eabi-gcc`)
- GNU Make
- STM32CubeIDE or another compatible development environment
- ST-LINK debugger/programmer
- STM32 development board (NUCLEO-F446RE)

Additional dependencies may be required as the project develops.

### Installation

Clone the repository:

```bash
git clone https://github.com/mei-tate/CustomRTOS.git
```

Navigate into the project directory:

```bash
cd CustomRTOS
```

### Building and Running

Build instructions will be added once the project build system and flashing workflow are finalized.

### Configuration

Configuration options will be documented as the kernel develops. Planned configuration settings may include:

- Maximum number of tasks
- Task stack sizes
- Task priorities
- System tick frequency
- Scheduler configuration

## Code Example

An example demonstrating task creation and execution will be added once the core task management and scheduling APIs are implemented.

The intended interface may look similar to the following:

```c
void task1(void *argument)
{
    while (1)
    {
        // Task implementation
    }
}

int main(void)
{
    // Initialize hardware and kernel

    // Create tasks
    // Start scheduler

    while (1)
    {
    }
}
```

*Note: This is an illustrative example, not a finalized API.*

## API Reference

See the [API Reference](docs/API.md) for documentation of kernel functions, data structures, and configuration options.

Documentation will be expanded as the public kernel interface is implemented.

## Project Structure

The project directory will follow a modular organization separating kernel functionality, hardware-specific code, application examples, and documentation.

```text
CustomRTOS/
├── docs/
│   └── API.md
├── include/
│   └── (kernel headers)
├── kernel/
│   └── (kernel implementation)
├── port/
│   └── stm32f446re/
│       └── (hardware-specific code)
├── examples/
│   └── (example applications)
├── tests/
│   └── (tests and validation)
├── README.md
└── Makefile
```

*Note: This is a proposed project structure and may change during development.*

## Development Roadmap

- [ ] Initialize the STM32 development environment
- [ ] Implement basic kernel initialization
- [ ] Define the Task Control Block (TCB)
- [ ] Implement task creation
- [ ] Implement the scheduler
- [ ] Implement context switching
- [ ] Integrate hardware timer interrupts
- [ ] Implement preemptive multitasking
- [ ] Add synchronization primitives
- [ ] Develop example applications
- [ ] Test and evaluate scheduling behavior

## References

- [STMicroelectronics STM32F446RE Product Page](https://www.st.com/en/microcontrollers-microprocessors/stm32f446re.html)
- [STM32 NUCLEO-F446RE User Manual (UM1724)](https://www.st.com/resource/en/user_manual/um1724-stm32-nucleo64-boards-mb1136-stmicroelectronics.pdf)
- [ARM Cortex-M4 Technical Reference Manual](https://developer.arm.com/documentation/100166/latest/)
- [ARM Cortex-M4 Devices Generic User Guide](https://developer.arm.com/documentation/dui0553/latest/)
