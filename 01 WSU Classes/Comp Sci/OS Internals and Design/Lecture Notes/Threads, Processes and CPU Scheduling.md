Class: [[OS Internals and Design]]
Date: 09-15-2025
Topics: 

## **Threads vs Processes**  

- **Process:** Execution context with its own address space, PCB (Process Control Block), and system resources.  
- **Thread:** Lighter-weight execution context that shares process resources (address space, open files, etc.).  

### Key Distinctions  
- **Process creation** (`fork()`) is more expensive than **thread creation** (`pthread_create()`).  
- Threads in a process share memory → lower overhead context switching.  
- **Schedulable entity:** Modern OS kernels (Windows NT, Linux) schedule *threads*, not entire processes.  

---

## **Threading Models**  

### **1. Many-to-One Model**
- **Mapping:** `N` user threads → **1 kernel thread**  
- **Characteristics:**  
  - Thread management entirely in **user space**.  
  - Kernel unaware of multiple threads (schedules process as a single schedulable entity).  
  - Context switches between threads do **not** trap to kernel.  
- **Advantages:**  
  - Minimal kernel involvement → **low context-switch overhead**.  
  - Scales well with many threads (from a memory overhead perspective).  
- **Disadvantages:**  
  - **No parallelism:** cannot utilize multiple CPU cores.  
  - One blocked thread (e.g., on system call) blocks entire process.  

---

### **2. One-to-One Model**
- **Mapping:** `1` user thread → `1` kernel thread  
- **Characteristics:**  
  - Thread creation calls into kernel to create a corresponding **KLT** (Kernel-Level Thread).  
  - True concurrency possible if multiple cores are available.  
- **Advantages:**  
  - **Parallel execution:** threads may be scheduled on multiple cores simultaneously.  
  - If one thread blocks, others can still run (since they have independent KLTs).  
- **Disadvantages:**  
  - Higher kernel overhead: OS must maintain a KLT for every ULT (User-Level Thread).  
  - Excessive thread creation may degrade system performance.  
- **Example OS:** Linux NPTL (Native POSIX Thread Library), Windows threads.  

---

### **3. Many-to-Many Model**
- **Mapping:** `M` user threads → `N` kernel threads (where `N ≤ M`)  
- **Characteristics:**  
  - OS dynamically maps user threads to available kernel threads.  
  - Allows concurrency without requiring a 1:1 mapping.  
- **Advantages:**  
  - Better scalability than 1:1 when many threads are created.  
  - OS can limit number of KLTs based on available resources.  
- **Disadvantages:**  
  - Implementation complexity (runtime must manage scheduling between ULTs and KLTs).  
  - Harder for programmer to predict scheduling behavior.  
- **Variants:**  
  - Two-level models (e.g., Solaris threads) that combine many-to-many with user-specified binding of ULT → KLT.  

---

## **Thread Scheduling and Context Switching**
- **Context Switch Components:**  
  - Save/restore CPU registers.  
  - Switch kernel stack and memory mapping (if process switch).  
  - Update scheduling queues.  
- **Thread scheduling** is finer-grained than process scheduling.  
- **Modern OS:** Kernel scheduler (e.g., Completely Fair Scheduler in Linux) chooses which KLT to run.  

---

## **CPU Scheduling Concepts**

### **When Scheduling Occurs**
- Running → Waiting (I/O request, semaphore wait).  
- Running → Ready (preemption).  
- Waiting → Ready (I/O completion).  
- Termination.  

### **Scheduling Criteria (Optimization Metrics)**  
| **Metric** | **Definition** | **Goal** |
|-----------|---------------|---------|
| **CPU Utilization** | % of time CPU is executing instructions (not idle) | Maximize |
| **I/O Utilization** | % of time I/O devices are actively servicing requests | Maximize |
| **Throughput** | # of processes completed per unit time | Maximize |
| **Turnaround Time** | Time from process creation → termination | Minimize |
| **Waiting Time** | Total time process spends in ready queue | Minimize |
| **Response Time** | Time from request → first CPU execution | Minimize (critical for interactive systems) |

---

## **Preemptive vs Non-Preemptive Scheduling**
- **Preemptive:** OS can forcibly deschedule a thread (e.g., time-slice expiry, higher-priority thread becomes ready).  
- **Non-Preemptive:** Threads voluntarily yield CPU (cooperative multitasking).  

---

## **Short-Term Scheduling Algorithms (Preview)**  
- **FCFS (First-Come, First-Served):** Simple FIFO queue; non-preemptive.  
- **SJF (Shortest Job First):** Optimal for minimizing waiting time (provably minimal average wait).  
- **Round Robin:** Preemptive; fixed quantum per process → good for interactive systems.  
- **Priority Scheduling:** Chooses highest-priority thread; risk of starvation without aging.  
