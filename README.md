# The Sensemakerer
## About the Project
This is a short, hacky project that uses email newsletters (Tortoise's [Daily Sensemaker](https://www.tortoisemedia.com/sensemakers/)) to fine tune a GPT-3 (`davinci`) model.

This model can then produce newsletters using an email subject as the prompt.

## Files
There are two main Jupyter notebooks:

### `data_production.ipynb`
1. Reads an email inbox (I produced it using Google Takeout).
2. Cleans up the data.
3. Produces the fine-tuning data in the appropriate `.jsonl` format.
4. Runs the bash commands using the OpenAI API to fine-tune an instance of davinci.

### `api_calls.ipynb`
1. Defines utility functions to produce and render api calls to fine-tuned models.
2. Contains logic to save function calls to a local `.pkl` file.

## Notes
- Fine-tuning an OpenAI model isn't free: 300 prompt-completion pairs (200-300 tokens ea.) cost me ~$20. If cost is a limiting factor you can train on cheaper models - [pricing info](https://openai.com/api/pricing/)
- This project, (and the OpenAI API) expect the API key to be saved as `$OPENAI_API_KEY`.