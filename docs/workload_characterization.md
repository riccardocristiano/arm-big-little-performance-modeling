# Workload Characterization

The first stage of the project analyses execution-time traces for heavy- and low-computation tasks running on the two processor types of an ARM big.LITTLE architecture.

## Trace Definitions

| Trace | Workload | Processor |
|---|---|---|
| `traceB-HH` | Heavy computation | High-Performance Core |
| `traceB-HE` | Heavy computation | Energy-Efficient Core |
| `traceB-LH` | Low computation | High-Performance Core |
| `traceB-LE` | Low computation | Energy-Efficient Core |

Each trace contains **50,000 observations**.

---

## Descriptive Statistics

| Trace | Mean | Std. Dev. | Median | CV | Skewness | Kurtosis |
|---|---:|---:|---:|---:|---:|---:|
| HH | 24.12551 | 35.19614 | 12.94626 | 1.458876 | 4.010614 | 23.78139 |
| HE | 96.56053 | 141.7805 | 51.45061 | 1.468307 | 4.067531 | 25.14491 |
| LH | 1.502497 | 0.4334404 | 1.46112 | 0.288480 | 0.5930218 | 0.5330907 |
| LE | 4.804131 | 1.382836 | 4.66398 | 0.287843 | 0.5692074 | 0.4393974 |

The heavy-computation traces have coefficients of variation greater than one and exhibit strong positive skew and high kurtosis.

The low-computation traces have coefficients of variation below one and are substantially more concentrated around their means.

---

## Distribution Analysis

Candidate distributions were investigated using:

- empirical PDFs
- empirical CDFs
- Q-Q plots
- coefficient-of-variation characteristics
- analytical parameter estimation
- method-of-moments reasoning

The candidate families considered in the report include:

- Hyper-exponential
- Hypo-exponential
- Erlang
- Gamma
- Normal
- Weibull

---

## Service-Time Models Used in Simulation

The service-time models subsequently used in the JMT queueing model were:

```text
S_HH ~ Gamma(k = 0.469854, θ = 51.346823)

S_HE ~ Gamma(k = 0.463838, θ = 208.1773)

S_LH ~ Gamma(k = 12.016235, θ = 0.1250389)

S_LE ~ Gamma(k = 12.257007, θ = 0.394983)
```

These distributions represent the four combinations of workload class and processor type.

---

## Note on the Original Report

The conclusion text in the original report states that the two heavy-computation traces are distributed according to a hyper-exponential model.

However, the parameter equations presented immediately below that statement, and the service-time definitions used later in the JMT model, specify **Gamma distributions for all four processor/workload combinations**.

This repository therefore documents the Gamma service-time models actually used in the system simulation.
