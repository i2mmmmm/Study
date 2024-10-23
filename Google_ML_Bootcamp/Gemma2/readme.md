## Gemma sprint


```python
# Install necessary libraries
!pip install transformers --quiet

# Import libraries
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

# huggingface login
from huggingface_hub import login
login("your_huggingface_token")


# Load the model and tokenizer
model_name = 'mmmmmlee/gemma2_2B_counseling_trainer'

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

# Define the function to generate advice (same as before)
FastLanguageModel.for_inference(model)
inputs = tokenizer(
    [
        alpaca_prompt.format(
            "너는 누구니?",  # 상담사 질문
            "", # input
            "",  # output
        )
    ],
    return_tensors="pt",
).to("cuda")


text_streamer = TextStreamer(tokenizer)
_ = model.generate(
    **inputs,
    streamer=text_streamer,
    max_new_tokens=128,  # 최대 생성 토큰 수 설정
    stopping_criteria=stopping_criteria


```
