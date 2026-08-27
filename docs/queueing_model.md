# Closed Multi-Class Queueing Model

The ARM big.LITTLE architecture was represented as a closed multi-class queueing network using **JMT (Java Modelling Tools)**.

## Job Classes

Two job classes are represented:

- heavy-computation tasks
- low-computation tasks

The project uses a closed model because the number of jobs circulating in the system is fixed.

The model specifies populations of:

```text
Heavy-computation jobs: 20
Low-computation jobs:   32
```

---

## System Workflow

Both classes follow the same general processing structure:

```text
Processor
   ↓
Storage
   ↓
I/O or Network
   ↓
Processor
```

The processor stage can be served by either:

- High-Performance Cores
- Energy-Efficient Cores

---

## High-Performance Cores

Configuration:

```text
Servers: 8
Queue capacity: Infinite
Scheduling: FCFS
```

Service-time distributions:

```text
Heavy:
Gamma(k = 0.469854, θ = 51.346823)

Low:
Gamma(k = 12.016235, θ = 0.1250389)
```

---

## Energy-Efficient Cores

Configuration:

```text
Servers: 4
Queue capacity: Infinite
Scheduling: FCFS
```

Service-time distributions:

```text
Heavy:
Gamma(k = 0.463838, θ = 208.1773)

Low:
Gamma(k = 12.257007, θ = 0.394983)
```

---

## Storage

Configuration:

```text
Servers: 1
Queue capacity: Infinite
Scheduling: Processor Sharing
```

Service times:

```text
Heavy:
Exp(λ = 5)

Low:
Exp(λ = 100)
```

---

## I/O

Configuration:

```text
Servers: 1
Queue capacity: Infinite
Scheduling: Processor Sharing
```

Service times:

```text
Heavy:
Exp(λ = 20)

Low:
Exp(λ = 6.667)
```

---

## Network

Configuration:

```text
Servers: 1
Queue capacity: Infinite
Scheduling: Processor Sharing
```

Service times:

```text
Heavy:
Exp(λ = 200)

Low:
Exp(λ = 8.333)
```

---

## Performance Measures

The JMT simulations were evaluated primarily through:

- local utilization
- local residence time
- local response time

These measures were subsequently used in the routing-probability what-if analysis.
