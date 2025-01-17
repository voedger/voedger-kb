# Software Engineering

- **Software Engineering**: Theory and practice of applying systematic methods for building reliable software.
- **Systematic method**: Step-by-step approach that follows a predefined set of principles and procedures to achieve consistent results.


## Overview

**Software Engineering** includes:

- Requirements engineering
- Software design and architecture
- Programming/coding - The actual implementation of software
- Testing and quality assurance
- Project management
- Software maintenance
- Configuration management
- Software documentation

Software Engineering is both a knowledge domain and an activity domain.

As a **Knowledge Domain**:
- Includes established best practices, patterns, and architectural approaches
- Contains bodies of knowledge like SWEBOK (Software Engineering Body of Knowledge)
- It encómpasses theoretical foundations, principles, and methodologies
- Builds on computer science theory, mathematics, and engineering principles
- Incorporates knowledge about process models, tools, and techniques
- Includes understanding of software quality attributes and metrics
- Covers theoretical aspects of testing, verification, and validation

As an **Activity Domain**:
- Involves practical application of software development methods
- Includes actual development and maintenance of software systems
- Encompasses project management and team coordination activities
- Involves real-world problem-solving and decision-making
- Includes concrete activities like coding, testing, and deployment
- Requires active stakeholder communication and requirement gathering
- Involves practical system design and architecture implementation

The interplay between these domains is crucial - the knowledge domain informs how activities should be carried out, while experiences from activities help evolve and refine the knowledge domain. This dual nature is what makes software engineering a rich and complex field that requires both theoretical understanding and practical skills.óó


## Principles

- Result should me measurable, if possible (metrics)
- Avoid dynamic anti-pátterns

## Dynamic anti-patterns

**Dynamic anti-patterns**: code patterns that lead to the degradation of performance, reliability, or maintainability.

Cause: Dynamic anti-patterns often stem from poorly designed concurrency control, resource handling, or error-handling mechanisms. Even if the initial architecture seems correct, **runtime behavior** can reveal significant inefficiencies (like busy waiting) or hidden faults. Addressing them involves:

- Using **proper synchronization** techniques (locks, semaphores, wait/notify, etc.).  
- Avoiding **polling** where event-driven approaches are possible.  
- Employing **resource pooling**, **backpressure**, and **circuit breakers** to keep the system healthy under variable load.  
- Ensuring **clean-up** and **monitoring** of all resources to prevent leaks or meltdown conditions.

---

### Busy Waiting (Spin Waiting)
- **What it is:** A thread (or process) constantly checks for a condition in a loop instead of blocking or yielding.  
- **Why it’s bad:** Consumes CPU cycles unnecessarily, leading to higher resource utilization and possible starvation of other threads.  
- **Better approach:** Use proper synchronization constructs like semaphores, mutexes, events, or condition variables that allow the waiting thread to sleep until notified.
---

### Memory Leaks & Resource Leaks
- **What it is:** Failing to release memory or other resources (like sockets, file handles) after use, resulting in gradually growing usage.  
- **Why it’s bad:**  
  - Eventually starves the system of memory or OS handles.  
  - Leads to performance degradation and potential crashes over time.  
- **Better approach:**  
  - Use try-with-resources, RAII (Resource Acquisition Is Initialization), or automatic memory management where possible.  
  - Ensure you always close or release resources in finally blocks (in languages where manual resource management is needed).

---

### Sleep-Based Polling
- **What it is:** The program periodically calls `sleep(...)` (or similar) to wait before re-checking a condition (e.g., “sleep for 500ms and check again”).  
- **Why it’s bad:**  
  - Creates arbitrary latency (the condition might be ready right after the thread goes to sleep).  
  - Wastes CPU when the sleep intervals are too short, or increases response time when intervals are too long.  
- **Better approach:** Use event-driven approaches or blocking I/O. Let threads block on condition variables or use asynchronous callbacks to be notified.

---

### Unbounded Concurrency
- **What it is:** A system that creates new threads or processes without limits for each incoming request or task, lacking mechanisms to control resource consumption.
- **Why it's bad:**
  - Can exhaust system resources (CPU, memory, file descriptors)
  - Leads to thrashing when too many threads compete for resources
  - Performance degradation due to excessive context switching
  - May cause system crashes or unresponsiveness
  - Unpredictable behavior under high load
- **Better approach:**
  - Implement thread pools with fixed or configurable maximum sizes
  - Use work queues to manage incoming tasks
  - Apply backpressure mechanisms to handle overload
  - Set appropriate resource limits and monitoring
  - Consider non-threaded approaches like event loops or async I/O

---

### Lock Contention & Lock Convoys
- **What it is:** Multiple threads frequently compete for the same lock, causing threads to line up waiting (a "convoy").  
- **Why it's bad:**
  - Throttles concurrency as threads become serialized around the lock
  - Performance degrades as more threads join the convoy
  - Creates unnecessary context switching overhead
  - Can lead to priority inversion problems
  - Increases overall system latency
- **Better approach:**
  - Reduce shared data or protected regions
  - Use more fine-grained locks or lock-free data structures
  - Redesign critical sections to be shorter
  - Consider alternative synchronization mechanisms like read-write locks
  - Implement lock striping for better concurrency
  - Use thread-local storage where possible

---

### Excessive or Repeated Resource Acquisition
- **What it is:** A loop or frequently invoked method repeatedly acquires the same expensive resource (database connection, file handle, etc.) instead of reusing or pooling.  
- **Why it’s bad:** Causes significant overhead from repeated opens/closes or handshakes.  
- **Better approach:**  
  - Use resource pooling (e.g., connection pools, object pools).  
  - Cache resources if they are reusable.

---

### Fire-and-Forget Without Feedback
- **What it is:** Spawning asynchronous tasks or network requests without checking success/failure status.  
- **Why it’s bad:**  
  - Errors or failures might go unnoticed, leading to data inconsistency or lost work.  
  - Harder to debug and maintain.  
- **Better approach:**  
  - Provide callbacks, futures/promises, or logs/metrics.  
  - Use acknowledgments or success/failure handlers to track completion.

---

### Thundering Herd
- **What it is:** Multiple concurrent processes/threads wake up to handle an event, but only one can actually process it, causing others to waste resources attempting to handle the same event.
- **Why it's bad:**
  - Wastes system resources as multiple processes compete unnecessarily
  - Can cause significant performance degradation under high load
  - Creates unnecessary context switching overhead
  - May lead to resource exhaustion in extreme cases
- **Better approach:**
  - Implement leader/follower pattern where one process handles events
  - Use semaphores instead of regular mutex locks
  - Implement request coalescing to handle multiple similar requests as one
  - Design systems to wake only necessary number of workers
  - Use event notification mechanisms that support exclusive wake-ups

---

### Cascading Failures
- **What it is:** A failure in one component causes increased load or resource strain in others, which in turn fail and propagate the problem system-wide.  
- **Why it’s bad:**  
  - Produces a domino effect of outages or slowdowns.  
- **Better approach:**  
  - Implement circuit breakers or fallback mechanisms.  
  - Design the system with bulkheads (isolation boundaries) and degrade gracefully.  
  - Monitor resource usage and errors to trigger fail-safe modes early.

---

### Request/Response Amplification
- **What it is:** A single incoming request causes an explosion of downstream calls or queries (e.g., microservices that keep fanning out).  
- **Why it’s bad:**  
  - Can cause high latency or resource use.  
  - Makes the system brittle under load spikes.  
- **Better approach:**  
  - Use caching or data aggregation patterns.  
  - Consolidate or batch requests.  
  - Employ service mesh or gateway to manage concurrency and rate-limiting.

## Glossary

**Backpressure** is a feedback mechanism where downstream components signal their processing capacity limits to upstream components, causing them to slow down or modify their data transmission rate to prevent system overload.

**Circuit breakers** are software components that monitor system failures and automatically prevent further requests to a failing service for a set time period, allowing it to recover while providing immediate fallback responses to clients.

**Polling** is a technique where a system repeatedly checks for state changes, data availability, or conditions at fixed intervals rather than receiving notifications when changes occur.