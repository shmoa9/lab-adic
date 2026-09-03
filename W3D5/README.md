# Lab W3D5: the benchmark harness

## Predict

As concurrency rises, throughput (tokens/s) climbs, then flattens; p95 latency is flat at low concurrency, then climbs. Your knee (where p95 crosses target as throughput stops rising) will be at about concurrency :  → *16*

Pick a target: p95 end-to-end latency of: → *2.0 seconds*. This is your SLO for today.

## Results

| Concurrency | Throughput (tokens/s) | TTFT p95 (s) | Latency p95 (s) | Errors |
|---:|---:|---:|---:|---:|
| 1 | 87.43 | 0.067 | 1.475 | 0 |
| 2 | 163.65 | 0.101 | 1.535 | 0 |
| 4 | 274.76 | 0.143 | 1.720 | 0 |
| 8 | 438.59 | 0.171 | 2.089 | 0 |
| 16 | 685.13 | 0.253 | 2.422 | 0 |

- *Model:* Qwen/Qwen2.5-1.5B-Instruct-AWQ
- *Knee:* 4
- *Tokens/s:* 274.76
- *p95:* 1.7199s
- *Errors:* 0


## Verification 

<img width="437" height="102" alt="Screenshot 2026-09-03 142214" src="https://github.com/user-attachments/assets/d3fa2021-d507-4c9a-a0f4-f7ee8a496f43" />


# Extra Lab W3D5: cost per million tokens and the scale-out breakeven

##  Results

| Concurrency | Throughput (tok/s) | p95 (s) | Cost / 1M tokens |
|---:|---:|---:|---:|
| 1 | 87.43 | 1.475 | $1.1120 |
| 2 | 163.65 | 1.535 | $0.5941 |
| 4 | 274.76 | 1.720 | $0.3538 |
| 8 | 438.59 | 2.089 | $0.2217 |
| 16 | 685.13 | 2.422 | $0.1419 |

## Scale-Out Plan

| Required Throughput | Replicas Needed | Total Cost / Hour | Effective p95 |
|---|---:|---:|---:|
| 274.76 tok/s (1×) | 1 | $0.35 | 1.7199s |
| 412.14 tok/s (1.5×) | 2 | $0.70 | 1.7199s |
| 549.52 tok/s (2×) | 2 | $0.70 | 1.7199s |
| 824.28 tok/s (3×) | 3 | $1.05 | 1.7199s |


## Verification 
<img width="448" height="87" alt="Screenshot 2026-09-03 142711" src="https://github.com/user-attachments/assets/f5b3075f-dccb-47b2-b9b9-9b83fa1e201b" />




