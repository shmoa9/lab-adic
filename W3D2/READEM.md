#. Lab W3D2: inference anatomy 


## Prediction Card (By Hand)

-Time to first token (TTFT) is dominated by prefill (reading the whole prompt). A longer prompt makes TTFT go →  up
- After the first token, decode emits one token at a time. The mean gap between tokens (TPOT) depends mostly on → model size
  and memory bandwidth
- KV cache math for Qwen2.5-1.5B: 28 layers, 2 KV heads, head_dim 128, fp16.
   -   Per token → 28 KB/token
   - 4096-token context → ≈ 0.112 GB KV cache
- Static batching: if you pad 8 prompts of different lengths and run them as one batch, the batch finishes
  when the  → the batch finishes when the slowest / longest prompt finishes.

## Results

### TTFT Scaling (Prefill):
- 128 tokens: 0.0375s
- 512 tokens: 0.0673s
- 2048 tokens: 0.3234s 

### TPOT (Decode):
  0.0379s/token


### Static Batching Straggler Tax:
- Batch 1: 28.2 tok/s (Slot efficiency: 1.000)
- Batch 4: 41.6 tok/s (Slot efficiency: ~0.344)
- Batch 8: 81.1 tok/s (Slot efficiency: ~0.344)


###  KV Formula Validation: Measured 28.0 KB/token vs Theoretical 28.0 KB/token (PASS).

  <img width="446" height="100" alt="Screenshot 2026-08-31 150026" src="https://github.com/user-attachments/assets/74849121-c304-456a-9100-8fbc23cb3941" />



## Inference Anatomy Baselines
baselines.json  ,, kv_check.json



