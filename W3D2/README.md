## Lab W3D2: inference anatomy 


## Prediction Card (By Hand)

- Time to first token (TTFT) is dominated by prefill (reading the whole prompt). A longer prompt makes TTFT go →  up
- After the first token, decode emits one token at a time. The mean gap between tokens (TPOT) depends mostly on → model size
  and memory bandwidth
- KV cache math for Qwen2.5-1.5B: 28 layers, 2 KV heads, head_dim 128, fp16.
   -   Per token → 28 KB/token
   - 4096-token context → ≈ 0.112 GB KV cache
- Static batching: if you pad 8 prompts of different lengths and run them as one batch, the batch finishes
  when the  → the batch finishes when the slowest / longest prompt finishes.

## Results

### TTFT Scaling :
- 128 tokens: 0.0375s
- 512 tokens: 0.0673s
- 2048 tokens: 0.3234s 

### TPOT :
- 0.0379s/token


### Static Batching Straggler Tax :
- Batch 1: 28.2 tok/s (Slot efficiency: 1.000)
- Batch 4: 41.6 tok/s (Slot efficiency: ~0.344)
- Batch 8: 81.1 tok/s (Slot efficiency: ~0.344)


###  KV Cache Footprint Verification: (PASS).

<img width="446" height="100" alt="Screenshot 2026-08-31 150026" src="https://github.com/user-attachments/assets/0970e789-0ab1-4794-8a9f-807d61485918" />


## Extra Lab W3D2: the paged KV allocator

## Prediction Card (By Hand)
- Fraction of unused reserved slab (4096 max vs 300 avg)  → 90%
- Blocks needed for a 300-token sequence (block size 16)  → 19 blocks.
- Blocks needed for a 4096-token sequence (block size 16) → 256 blocks.

  ## KV Cost

-  28 KB/token  
-  448 KB/block

## Result

- Naive Slab   : 18 admitted  , 42 rejected  
- Block-Pool   : 60 admitted  , 0 rejected

  ### Block-Pool Advantage: 3.33x
  ### Verification:
  
  <img width="452" height="76" alt="Screenshot 2026-08-31 154721" src="https://github.com/user-attachments/assets/35dd7ba3-f834-4cbd-bf8b-5ace26bc0fcf" />



