## 🚀 Purchase Your Permanent Offline License
https://buy.stripe.com/4gM4gsbwd0Hv2Tg6ZN9R600
# pyr-AI-Enterprise
pyr is a fully offline, air-gapped AI synthesis platform for generating production-ready codebases and native PowerPoint presentations without cloud API connections.
# pyr

`pyr` is a fully offline, self-contained AI synthesis platform for generating production-ready codebases, multi-stage microservices, and native PowerPoint presentations (`.pptx`) from optimized prompts.

## What it does

- Provides an interactive web dashboard for entering requirements, attaching reference files (for design system and architecture mirroring), and generating a **compiled prompt** envelope.
- Ingests the compiled payload, executes local `.gguf` AI models entirely offline via `llama-cpp-python`, writes files into `sandbox_outputs/<project_name>`, and validates generated code with autonomous self-repair.
- Is a convenience driver that runs the entire end-to-end cycle and prints the audit summary.

## Requirements

- Included `gemma4:12b` in models directory.


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
4. The default username and passwords would spin up in the terminal. admin/admin123 if totally lost.


## 🤖 How to Add or Upgrade AI Models

`pyr` is a 100% offline application and will never connect to the internet to download AI model files automatically. To add or upgrade models for your local engine:

1. **Download a Model:** Visit HuggingFace in your web browser and download any `.gguf` formatted model file (we highly recommend `Qwen2.5-7B-Instruct.gguf` or `Gemma-2-9B-It.gguf`).
2. **Drop into Models Folder:** Open your `pyr` application directory and move the downloaded `.gguf` file directly into the `models/` folder.
3. **Select in Dashboard:** Refresh your `pyr` web dashboard. The new model will instantly appear in the Model Selection dropdown menu!
