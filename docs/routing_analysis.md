# Routing Probability Analysis

The queueing-network model depends on routing probabilities that determine how jobs move between Storage, I/O, Network, High-Performance Cores, and Energy-Efficient Cores.

A parametric **what-if analysis** was therefore performed in JMT.

## Performance Indicators

For each routing configuration, the following local measures were examined:

- utilization
- residence time
- response time

The probabilities investigated controlled routing between:

- Storage and I/O
- Storage and Network
- I/O and High-Performance Cores
- I/O and Energy-Efficient Cores
- Network and High-Performance Cores
- Network and Energy-Efficient Cores

---

## Main Observations

The simulations showed that routing decisions strongly affect the processor stations.

In particular:

- High-Performance Core utilization increases when more computation-heavy workload is directed toward HPC.
- Energy-Efficient Cores can become highly utilized and develop large residence or response times when excessive workload is directed toward them.
- Storage, I/O, and Network generally remain less utilized than the processing cores.
- The Energy-Efficient Cores frequently behave as the critical resource in poorly balanced routing configurations.

---

## Selected Routing Probabilities

The final routing configuration was chosen as:

### After Storage

```text
10% → I/O
90% → Network
```

for both workload classes.

### After I/O

```text
90% → High-Performance Cores
10% → Energy-Efficient Cores
```

for both workload classes.

### After Network

```text
90% → High-Performance Cores
10% → Energy-Efficient Cores
```

for both workload classes.

Equivalently:

```text
p34H = p34L = 0.10
p35H = p35L = 0.90

p41H = p41L = 0.90
p42H = p42L = 0.10

p51H = p51L = 0.90
p52H = p52L = 0.10
```

---

## Final Utilization

For the selected routing configuration, the report gives the following processor utilizations.

### Heavy-computation workload

```text
HPC = 0.8339
EFC = 0.7377
```

### Low-computation workload

```text
HPC = 0.144
EFC = 0.1017
```

The non-processing stations remain substantially less utilized.

---

## Residence Time

The report identifies the processing cores as the stations with the highest residence times.

The High-Performance Cores are reported at approximately:

```text
45.019
```

while the Energy-Efficient Cores are reported at approximately:

```text
19.3712
```

with considerably lower residence times at the communication and storage stations.

---

## Response-Time Behaviour

The Energy-Efficient Cores show higher response-time values than the High-Performance Cores, particularly for heavy-computation jobs.

For Network traffic, the report also highlights a larger response-time contribution for low-computation jobs:

```text
Φ_L ≈ 0.1318

Φ_H ≈ 0.00557
```

The final results therefore illustrate the trade-off between using energy-efficient processing resources and maintaining low response times.
