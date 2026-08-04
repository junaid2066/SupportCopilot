# E-commerce Support Copilot and Refund Portal

A Flask application for searching customer-support tickets, retrieving similar historical cases, generating AI-assisted responses, and recommending refunds.

## Main corrections in this revision

- Premium ChatGPT/Copilot-inspired responsive UI.
- Stable recommendation dictionary with both `probability` and `refund_probability`.
- Defensive Jinja access using `dict.get()` to prevent `UndefinedError`.
- Working ticket chat endpoint: `/api/tickets/<ticket_id>/chat`.
- Demonstration approve/reject workflow that does not execute financial transactions.
- Dataset validation for all 18 required columns.
- Optional Ollama or OpenAI response generation with a deterministic local fallback.

## Install and run on Windows

```powershell
cd "D:\Projects\e-commerce CSR and Refund agent\ecommerce_support_refund_agent"
conda activate customersupport
python -m pip install -r requirements.txt
python app.py
```

Open: http://127.0.0.1:5000

## Environment configuration

Copy `.env.example` to `.env` and adjust values as needed. The included dataset is used by default.

For Ollama:

```env
LLM_PROVIDER=ollama
OLLAMA_MODEL=llama3.1:8b
```

For no external LLM:

```env
LLM_PROVIDER=none
```

## Retrain models

```powershell
python train_models.py
```

The included refund approval route is a demonstration audit action only. It does not transfer money.
