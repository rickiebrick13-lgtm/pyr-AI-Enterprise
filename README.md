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

## How to Use the App

1. After authenication key is input into the app, you'll face a login screen.

2. The default username and passwords would spin up in the terminal. admin/admin123 , devuser/TestPass@123(for instantly jumping to sandbox) if totally lost.

3. Within, you'll see a "Return to sandbox" Button on the top right, click it.

<img width="1233" height="490" alt="image" src="https://github.com/user-attachments/assets/9be61555-25cd-4415-8eb5-75f62833aa24" />
4. This page is where everything happens:

<img width="1230" height="782" alt="image" src="https://github.com/user-attachments/assets/b684a6d3-1a5d-482c-b0ab-b1e140ca26da" />
5. Input your prompt into the raw prompt textbox. The prompt can be as vague as "Build a full-stack bike rental shop web app with FastAPI and MySQL. Receptionists register customers and rent/return bikes with daily rates.
 Managers see a dashboard of active rentals, overdue bikes, and revenue. Mechanics log maintenance jobs per bike (brake check, tire swap). Include schema.sql, HTML pages in FastAPI responses, and a simple stock count for helmets and locks with low-stock warnings. authentication needed. 
" or "Generate a PowerPoint workflow diagram for an E-commerce Order Fulfillment process. Steps: 'Order Received' (Sales lane), 'Payment Verification' (Finance lane), 'Inventory Check' (Warehouse lane), 'Packing' (Warehouse lane), and 'Shipping' (Logistics lane). Connect them sequentially. 
" , The more consise the better. 

6. Fill in the project name 

7. If you have a reference file, the model will use it as an example to follow to it's best ability 

7a. The checkboxes, Security Evaluation is not an cyber defense suite. It only scans for what is trained. 
7b. Agentic reflection is a multi-agent review for generated code 
7c. Model selection, as is name. Check it if you had loaded your own model into it 
7d. Staged Pipeline, It's a two pass code generator mode. Use it for fewer full stack mistakes 

8. Next under compile enrichments they're very literal 
<img width="1189" height="378" alt="image" src="https://github.com/user-attachments/assets/ae47ab96-3331-47f2-bc17-c59da26a71ee" />

9. Now advanced runner config, select your model, and context windows with max output tokens, each setting has a recommended RAM/VRAM tooltip 
<img width="1208" height="594" alt="image" src="https://github.com/user-attachments/assets/ddfc7715-89e6-48f3-b54c-afd1b6092398" />

10. Inference timeout is literally how much time you give for the model to work, note: if using staged pipeline, it will multiply by number of stages, but may or may not use up the time given 

11. Test timeout is for the testing of full stack code generated 

12. Target language, select your target language, python, Java, JavaScript, C#, C++, go and C11 or pptx if you're making a deck of powerpoint slides 

13. <img width="1219" height="462" alt="image" src="https://github.com/user-attachments/assets/86612eb6-2edb-4ef3-9257-351d3bdf8190" />

13a. Note: Models accuracy will follow the dropdown, lower, the worser, for C11, best to run it in a sandbox. 

14. Click compile and optimise, and this is a preview 

15. <img width="1178" height="633" alt="image" src="https://github.com/user-attachments/assets/78651a1c-2d45-4dfd-90ae-382149ff58e6" /> 

16. Click run model to and the model will spin up and load the layers into your VRAM and RAM 
<img width="2490" height="1066" alt="image" src="https://github.com/user-attachments/assets/83000856-91e2-47f8-8b1f-550bd9a61e3c" /> 

17. Once it is done, it will output files to the relevant folder with your selected project name 

18. If it fails, it will inform you can fail gracefully, checking the logs will tell you what is broken, but opening an IDE will also show. 

19. Even if it passes, there may be hidden errors, do check properly 

20. For PPTX, if for some reason the pptx file was not generated, run the python file generated in an IDE to spawn it. 

21. This app isn't good at front end design, but it'll handle most of the backend work. 

22. PPTX output for simple prompts 
<img width="1584" height="746" alt="image" src="https://github.com/user-attachments/assets/23a369fd-29da-4fa9-b7b7-cfa05d225bcd" />

23. Python output 
<img width="814" height="355" alt="image" src="https://github.com/user-attachments/assets/aa2c18e8-e03a-42f5-bfad-eedd9e06b02b" />

24. Expose of bad front end design 
<img width="696" height="519" alt="image" src="https://github.com/user-attachments/assets/9cdde59d-9ccf-42fd-a0e0-b4bf340ca6bd" />

25. Set-Location "c:\Users\your_username\...\pyr\sandbox_outputs\your_app_name".\start.bat for uvicorn 

26. swap .\start.bat with uvicorn main:app --reload --host 127.0.0.1 --port 8000 for development 

27. Otherwise, just run the app generated in the IDE, usually named main.language 



    



