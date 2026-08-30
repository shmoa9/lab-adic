# Lab W3D1: profile inference on a real GPU

## Results

| Dtype | Context | VRAM (GB) | GPU Util. | Tokens/s |
|---|---:|---:|---:|---:|
| FP16 | 512 | 3.113 | 54.3% | 29.8 |
| FP16 | 2048 | 3.295 | 45.8% | 19.9 |
| FP16 | 4096 | 3.568 | 88.7% | 26.1 |
| INT8 | 512 | 1.805 | 24.2% | 5.6 |
| INT8 | 2048 | 2.035 | 26.5% | 5.5 |
| INT8 | 4096 | 2.309 | 30.3% | 5.2 |

## Batch Experiment

<img width="620" height="67" alt="Screenshot 2026-08-30 153550" src="https://github.com/user-attachments/assets/ef0b7ed2-f29e-4d04-b316-1fa3db2f3754" />


## Verification

<img width="432" height="93" alt="Screenshot 2026-08-30 151233" src="https://github.com/user-attachments/assets/a1ea6538-0948-4a32-bd4b-0466f9ab2989" />
