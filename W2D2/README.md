W2D2 – Model Serving API

This project wraps Qwen/Qwen2.5-0.5B-Instruct behind an OpenAI-compatible FastAPI service running on CPU.

Implemented Endpoints

* GET /health
* GET /v1/models
* POST /v1/chat/completions

Streaming is optional for this lab and is not implemented.

Run the Server

<img width="466" height="155" alt="Screenshot 2026-08-27 150705" src="https://github.com/user-attachments/assets/97281c58-8727-4787-8c2d-ce81854dbb17" />


Verify

From the project folder:

python verify.py

Verification Result

<img width="463" height="110" alt="Screenshot 2026-08-27 150719" src="https://github.com/user-attachments/assets/da53caf4-36bb-48a4-98fd-55c1a3fd390a" />


Model

Qwen/Qwen2.5-0.5B-Instruct

Notes

Model generation runs synchronously on CPU and blocks while generating. Concurrency is intentionally not handled in this week-2 implementation.
