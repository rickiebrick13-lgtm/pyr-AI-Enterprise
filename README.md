## 🚀 Purchase Your Permanent Offline License
https://buy.stripe.com/4gM4gsbwd0Hv2Tg6ZN9R600
# pyr-AI-Enterprise
pyr is a fully offline, air-gapped AI synthesis platform for generating production-ready codebases and native PowerPoint presentations without cloud API connections.
# pyr

`pyr` is a fully offline, self-contained AI synthesis platform for generating production-ready codebases, multi-stage microservices, and native PowerPoint presentations (`.pptx`) from optimized prompts.

## What it does

- `app.py` provides an interactive web dashboard for entering requirements, attaching reference files (for design system and architecture mirroring), and generating a **compiled prompt** envelope.
- `runner.py` ingests the compiled payload, executes local `.gguf` AI models entirely offline via `llama-cpp-python`, writes files into `sandbox_outputs/<project_name>`, and validates generated code with autonomous self-repair.
- `e2e_runner.py` is a convenience driver that runs the entire end-to-end cycle and prints the audit summary.

## Requirements

- Python 3.11+ (tested in the local workspace with Python 3.14)
- A local `.gguf` AI model file (e.g., `gemma4-12b.gguf`, `qwen2.5-7b-instruct.gguf`, or `gemma-2-9b-it.gguf`) placed directly in the `models/` directory.
- Included `gemma4:12b` in models directory.
- Copy `cred.env.example` to `cred.env` and set strong `FLASK_SECRET_KEY` / `JWT_SECRET` values (32+ chars).
- Install runtime dependencies with `pip install -r requirements.txt`

## Running the Web Dashboard

```bash
python app.py
```

Then open `http://127.0.0.1:5000` in your browser.

## Running the Runner Directly

The runner can accept a compiled prompt via stdin or load the latest payload from the local database.

```bash
python runner.py < payload.txt
```

## Running the E2E Harness

Use `e2e_runner.py` to execute the full flow from your current database payload into the sandbox, then print the audit summary.

```bash
python e2e_runner.py
```

If the app context is unavailable, the script will fall back to `test_ledger.db`.

## Audit output

Generated projects are written to `sandbox_outputs/<project_name>`.
Each generated project will include an `audit.json` file with:

- `project_name`
- `files_written`
- `ast_ok`
- `tests.present`
- `tests.passed`
- `tests.output`
- `written_at`

The Flask app also exposes a runner audit endpoint:

```
/runner/audit
```

Use `?project=<name>` to target a specific project directory, or omit it to fetch the most recent audit.

## Notes

- The system uses a strict JSON schema prompt template in `app.py` to reduce output ambiguity.
- `runner.py` performs AST validation, an optional test run, and an auto-repair loop when tests fail.
- If the runner fails, inspect `sandbox_outputs/runner.log` and `sandbox_outputs/raw_fault_payload.txt` first.

## 💼 Commercial Offline Licensing & Activation

`pyr` is built for maximum air-gap security and operates entirely offline without making external internet calls or license verification pings.

### For Users (Unlocking Your Copy)
1. On your very first launch, `pyr` will calculate a unique **Machine ID** (e.g., `PYR-9A4B-22F1-807C`) derived from your motherboard and CPU hardware signatures.
2. Copy this Machine ID and paste it into your purchase portal receipt page to instantly generate your **Offline Unlock Key**.
3. Paste the Unlock Key into `pyr` to permanently unlock the application on your workstation.

### For Sellers / MoR Integration
To generate license keys for your customers, run `offline_licensing.py` directly from your command line or link it to your MoR webhook (Lemon Squeezy/Paddle):
```bash
python offline_licensing.py <CUSTOMER_HARDWARE_ID>
```

## 🤖 How to Add or Upgrade AI Models

`pyr` is a 100% offline application and will never connect to the internet to download AI model files automatically. To add or upgrade models for your local engine:

1. **Download a Model:** Visit HuggingFace in your web browser and download any `.gguf` formatted model file (we highly recommend `Qwen2.5-7B-Instruct.gguf` or `Gemma-2-9B-It.gguf`).
2. **Drop into Models Folder:** Open your `pyr` application directory and move the downloaded `.gguf` file directly into the `models/` folder.
3. **Select in Dashboard:** Refresh your `pyr` web dashboard. The new model will instantly appear in the Model Selection dropdown menu!
