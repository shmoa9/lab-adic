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




