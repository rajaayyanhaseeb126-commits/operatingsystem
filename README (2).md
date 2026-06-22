# CPU Scheduling Simulator

A single-page web application that visually simulates four classic CPU scheduling algorithms with Gantt charts and performance metrics.

---

## Features

- **4 Scheduling Algorithms** — FCFS, SJF, Priority, and Round Robin
- **Interactive Gantt Chart** — color-coded, scrollable, with time markers
- **Performance Metrics** — Average Waiting Time, Average Turnaround Time, CPU Utilization
- **Per-Process Results Table** — Arrival, Burst, Start, Finish, WT, TAT
- **Sample Data Loader** — pre-filled examples for each algorithm
- **Zero dependencies** — pure HTML, CSS, and JavaScript; no install required

---

## Project Structure

```
cpu-scheduler/
└── index.html   ← entire application (HTML + CSS + JS)
```

---

## Setup & Running

### Option 1 — Open directly in browser (simplest)

```bash
# Just double-click index.html, or from terminal:
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### Option 2 — Serve with Python (recommended to avoid CORS quirks)

```bash
# Python 3
python3 -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080
```

Then open **http://localhost:8080** in your browser.

### Option 3 — Serve with Node.js

```bash
npx serve .
# or
npx http-server . -p 8080
```

Then open **http://localhost:8080**.

### Option 4 — VS Code Live Server

1. Install the **Live Server** extension in VS Code.
2. Right-click `index.html` → **Open with Live Server**.

---

## 📖 How to Use

### 1. Choose an Algorithm
Click one of the four tabs at the top:
- **First Come First Serve** — no extra input needed
- **Shortest Job First** — no extra input needed
- **Priority Scheduling** — enter a priority number (1 = highest priority)
- **Round Robin** — set the time quantum (default: 2 ms)

### 2. Add Processes
Fill in the fields and click **+ Add Process**:

| Field | Description |
|---|---|
| Arrival Time | When the process enters the ready queue (ms) |
| Burst Time | CPU time the process needs (ms) |
| Priority | Only for Priority Scheduling (1 = highest, higher number = lower priority) |

### 3. Run the Simulation
Click **▶ Run Simulation** to see:
- The **Gantt Chart** (scrollable if many processes)
- The **Results Table** with per-process metrics
- The **Summary Stats** (Avg WT, Avg TAT, CPU Utilization)

### 4. Quick Start with Sample Data
Click **Load Sample Data** to populate the ready queue with pre-built examples for the active algorithm.

---

## Algorithms Explained

### First Come First Serve (FCFS)
- Processes execute in arrival order.
- **Non-preemptive** — a running process is never interrupted.
- Simple but can cause the **convoy effect** (short jobs wait behind long ones).

### Shortest Job First (SJF)
- Among all arrived processes, the one with the **smallest burst time** runs next.
- **Non-preemptive** — once started, it runs to completion.
- Minimizes average waiting time but requires knowing burst times upfront.

### Priority Scheduling
- Each process is assigned a **priority** (1 = highest).
- The highest-priority ready process runs next; ties broken by arrival time.
- **Non-preemptive**. Low-priority processes may suffer **starvation**.

### Round Robin (RR)
- Each process gets a fixed **time quantum** in cyclic order.
- **Preemptive** — after the quantum expires the process returns to the queue.
- Fair and responsive; quantum size affects performance:
  - Large quantum → behaves like FCFS
  - Small quantum → higher context-switch overhead

---

## Metrics Defined

| Metric | Formula |
|---|---|
| Waiting Time (WT) | Start Time − Arrival Time |
| Turnaround Time (TAT) | Finish Time − Arrival Time |
| Average WT | Sum of all WT / Number of processes |
| Average TAT | Sum of all TAT / Number of processes |
| CPU Utilization | (Total Time − Idle Time) / Total Time × 100% |

> **Note for Round Robin:** Waiting Time = Finish Time − Arrival Time − Burst Time (accounts for multiple time slices).

---

## Browser Compatibility

| Browser | Supported |
|---|---|
| Chrome / Edge 90+ | ✅ |
| Firefox 88+ | ✅ |
| Safari 14+ | ✅ |
| Mobile browsers | ✅ (responsive layout) |

---
