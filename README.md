# task-scaffolding
Scaffolded Task Design for Identifying Reasoning Gaps in LLMs

## How to run 

### 1. **Clone the Repository**

First, clone the repository to your local machine:

```bash
git clone []
cd task-scaffolding
```

### 2. **Install Dependencies**

Create a new conda or Python virtual environment. Install all dependencies using pip:pip:

```bash
pip install -r requirements.txt
```

### 3. **Dataset**

You can upload the dataset in the `data/` directory. This is a JSONL file where each entry is a JSON with at least two fields, "question" and "answer." For example:

```json
{
   "question": "The conference began at 09:30:00 AM and concluded at 04:45:00 PM. Calculate the total elapsed time during the conference.",
   "answer": "7 hours 15 minutes"
}
```

### Run the script (Generating Test Cases)
Once your dataset is uploaded in the `data/` directory, you can generate variations for each question. 

Create a config.json file in your project root:
```
{
  "input_file": "data/sample_data.jsonl",
  "model_name": "gpt-oss-120b",
  "judge_model_name": "llama-3-3-70b",
  "Math-Verify": false,
  "client_type": "vllm"
}
```
And run the script:
```
python scripts/sub_task_analysis_all.py --config config.json
```


### 5. Run the script (Testing Cases)
Once the variations are created, you can test them with your model.

Create a config_debugging.json file in your project root:
```
{
  "input_file": "data/sample_data_final.jsonl",
  "debugging_model_name": "granite-3-3-8b",
  "judge_model_name": "llama-3-3-70b",
  "Math-Verify": false,
  "client_type": "vllm"
}
```
And run the script:
```
python scripts/sub_task_debugging.py --config config_debugging.json
```
