# Lab W3D3: the engine swap

## Prediction Card (By Hand)
* At concurrency 8, vLLM’s throughput will be about → 2.0x .
* Monday’s static batching scales from batch 1 to batch 8 by → 3.05x.
*  Predict how it scales from concurrency 1 to 8: → 3.5x.
* vLLM’s scaling multiple to be larger than static batching, and roughly → 1.15x larger.

## Results

| Concurrency | Baseline | vLLM | Speedup |
|---|---:|---:|---:|
| 1 | 32.4 tokens/s | 56.1 tokens/s | 1.73x |
| 4 | 48.0 tokens/s | 161.6 tokens/s | 3.37x |
| 8 | 98.9 tokens/s | 230.4 tokens/s | 2.33x |

## Scaling

 * Static batching scaling : *3.05x*
 * vLLM scaling : *4.11x*
 * vLLM scaling is *1.35x larger* 

   
## Verification 

<img width="375" height="74" alt="Screenshot 2026-09-01 140525" src="https://github.com/user-attachments/assets/1cb09f66-6cdc-41ba-8042-fd089c886031" />


# Extra Lab W3D3: Client-Side Load Shedding Under Overload

## Results

### 1. Unbounded Baseline vs. Load Shedding (Burst = 50)

| Strategy | Requests Sent | Accepted | Shed (Rejected) | p95 Latency (Accepted) | Mean Latency |
|---|---:|---:|---:|---:|---:|
| Naive (Unbounded) | 50 | 50 | 0 | 1.187 s | 1.158 s |
| Shedded (cap=8) | 50 | 8 | 42 | 0.910 s | — |

### 2. Load Shedding Sweep Across Burst Sizes (cap=8)

| Burst Size (N) | Accepted | Shed | Accepted p95 Latency |
|---:|---:|---:|---:|
| 8 | 8 | 0 | 0.465 s |
| 16 | 8 | 8 | 0.389 s |
| 32 | 8 | 24 | 0.408 s |
| 50 | 8 | 42 | 0.392 s |


### Verified
GREEN CHECK: PASS

<img width="464" height="88" alt="Screenshot 2026-09-01 154335" src="https://github.com/user-attachments/assets/de367e1e-1854-49af-883f-03649902ec38" />


