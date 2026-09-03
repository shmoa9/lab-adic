# Lab W3D5: the benchmark harness

## Predict

As concurrency rises, throughput (tokens/s) climbs, then flattens; p95 latency is flat at low concurrency, then climbs. Your knee (where p95 crosses target as throughput stops rising) will be at about concurrency : > → *16*
Pick a target: p95 end-to-end latency of: > → *2.0 seconds*. This is your SLO for today.

## Results

- *Model:* Qwen/Qwen2.5-1.5B-Instruct-AWQ
- *Knee:* 4
- *Tokens/s:* 274.76
- *p95:* 1.7199s
- *Errors:* 0


## Verification 

<img width="437" height="102" alt="Screenshot 2026-09-03 142214" src="https://github.com/user-attachments/assets/d3fa2021-d507-4c9a-a0f4-f7ee8a496f43" />


# Extra Lab W3D5: cost per million tokens and the scale-out breakeven

##  Results

| Result | Value |
|---|---|
| Cost per Million Tokens | $0.3538 |
| Scale-Out (2× Demand) | 2 replicas |
| Total Hourly Cost | $0.70/hr |


## Verification 
<img width="448" height="87" alt="Screenshot 2026-09-03 142711" src="https://github.com/user-attachments/assets/f5b3075f-dccb-47b2-b9b9-9b83fa1e201b" />




