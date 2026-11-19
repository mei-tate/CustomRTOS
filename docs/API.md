# API Reference Guide

This document provides an overview of the CustomRTOS kernel API, including function descriptions, parameters, return values, and usage examples.

The API is organized by functionality to make it easier to reference individual kernel components.

(This is just an idea of how to lay out this page; real function names, params, and uses will be added when implemented) 

---

## System Control

Functions responsible for initializing, starting, and controlling the RTOS kernel.

### Kernel Initialization

**Function:** `RTOS_Init()`

- **Description:** Initializes the RTOS kernel and prepares the system for task execution.
- **Parameters:** None
- **Returns:** None

### Start Scheduler

**Function:** `RTOS_Start()`

- **Description:** Starts the RTOS scheduler and begins executing scheduled tasks.
- **Parameters:** None
- **Returns:** None

### Kernel Tick

**Function:** `RTOS_Tick()`

- **Description:** Handles periodic system tick events used for scheduling and time management.
- **Parameters:** None
- **Returns:** None

### Critical Sections

**Function:** `RTOS_EnterCritical()`

- **Description:** Enters a critical section to prevent task switching or other specified kernel interruptions while accessing shared resources.
- **Parameters:** None
- **Returns:** None

**Function:** `RTOS_ExitCritical()`

- **Description:** Exits a critical section and restores normal kernel operation.
- **Parameters:** None
- **Returns:** None

---

## Task Management

Functions responsible for creating, scheduling, and managing individual tasks.

### Task Creation

**Function:** `RTOS_CreateTask()`

- **Description:** Creates a new task and initializes its Task Control Block (TCB), stack, and initial execution context.
- **Parameters:**
  - `taskFunction`: Pointer to the task's entry function.
  - `stack`: Pointer to the task's allocated stack.
  - `stackSize`: Size of the allocated stack.
  - `priority`: Priority assigned to the task.
- **Returns:** Status indicating whether task creation succeeded.

### Task Deletion

**Function:** `RTOS_DeleteTask()`

- **Description:** Removes a task from the scheduler and releases or invalidates its associated resources.
- **Parameters:**
  - `task`: Identifier or pointer to the task being deleted.
- **Returns:** Status indicating whether task deletion succeeded.

### Task State Management

**Function:** `RTOS_GetTaskState()`

- **Description:** Retrieves the current execution state of a specified task.
- **Parameters:**
  - `task`: Identifier or pointer to the task.
- **Returns:** Current task state.

**Function:** `RTOS_SuspendTask()`

- **Description:** Suspends a task, preventing it from being selected for execution.
- **Parameters:**
  - `task`: Identifier or pointer to the task.
- **Returns:** Status indicating whether the operation succeeded.

**Function:** `RTOS_ResumeTask()`

- **Description:** Resumes a previously suspended task, allowing it to become eligible for scheduling.
- **Parameters:**
  - `task`: Identifier or pointer to the task.
- **Returns:** Status indicating whether the operation succeeded.

### Task Priority

**Function:** `RTOS_SetTaskPriority()`

- **Description:** Changes the priority of an existing task.
- **Parameters:**
  - `task`: Identifier or pointer to the task.
  - `priority`: New task priority.
- **Returns:** Status indicating whether the operation succeeded.

**Function:** `RTOS_GetTaskPriority()`

- **Description:** Retrieves the priority assigned to a task.
- **Parameters:**
  - `task`: Identifier or pointer to the task.
- **Returns:** Task priority.

---

## Scheduling

Functions related to task selection and scheduler operation.

### Scheduler

**Function:** `RTOS_Schedule()`

- **Description:** Selects the next task to execute based on task priority and readiness.
- **Parameters:** None
- **Returns:** None

### Yield Processor

**Function:** `RTOS_Yield()`

- **Description:** Voluntarily gives up the processor so another eligible task can execute.
- **Parameters:** None
- **Returns:** None

---

## Time Management

Functions for managing system time and task delays.

### Task Delay

**Function:** `RTOS_Delay()`

- **Description:** Blocks the calling task for a specified number of system ticks.
- **Parameters:**
  - `ticks`: Number of system ticks to wait.
- **Returns:** None

### System Tick Count

**Function:** `RTOS_GetTickCount()`

- **Description:** Retrieves the current system tick count.
- **Parameters:** None
- **Returns:** Current system tick count.

---

## Data Types and Structures

Definitions of the primary data types used throughout the CustomRTOS API.

| Type | Description |
|---|---|
| `TCB` | Task Control Block containing task-specific information. |
| `TaskFunction` | Function pointer representing a task entry point. |
| `TaskState` | Enumeration of possible task execution states. |
| `TaskPriority` | Type representing task scheduling priority. |
| `RTOS_Status` | Status code returned by kernel operations. |

---

## Return Codes

| Code | Description |
|---|---|
| `RTOS_OK` | Operation completed successfully. |
| `RTOS_ERROR` | General operation failure. |
| `RTOS_INVALID_PARAM` | One or more parameters are invalid. |
| `RTOS_NO_MEMORY` | Insufficient memory to complete the operation. |
| `RTOS_TASK_LIMIT_REACHED` | Maximum number of tasks has been reached. |

---

## Usage Examples

Examples or links to examples demonstrating how to initialize the kernel, create tasks, configure priorities, and start the scheduler will be added as the API is implemented.
