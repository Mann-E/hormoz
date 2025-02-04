---
license: mit
language:
- en
- fr
- de
- es
- it
- pt
- ja
- ko
- zh
- ar
- el
- fa
- pl
- id
- cs
- he
- hi
- nl
- ro
- ru
- tr
- uk
- vi
datasets:
- xmanii/mauxi-talk-pro
- xmanii/mauxitalk-persian
---

# Hormoz 8B 

## Introduction

This model is an effort in order to make a multi-lingual and _on device_ models which can be executed on the consumer hardware. The model follows the steps used in training _DeepSeek_ model. However, the model is _not a reasoning model_ and a generic question answering, conversational and _uncensored_ model which has been made with a cost of around $4000 USD. 

If you're curious about the model you also can see our [GitHub](https://github.com/mann-e/hormoz) and learn more about the benchmarks and costs. 

Also, this model is based on _Command R_'s architecture, since that architecture gave us the best results in multilingual chat. Specially with languages such as _Persian_ and _Arabic_. This way, you can consider this model like a commercially useaeble version of _aya expanse_ as well.

### The name

<p align="center">
  <img src="https://github.com/Mann-E/hormoz/blob/main/hormoz-logo.png?raw=true" width=768px />
</p>

The name __Hormoz__ comes from the Persian word "هرمز" which has multiple meanings. It can point to the _strait of Hormoz_ in Persian Gulf or _Hormoz Island_ which is part of the Hormozgan Province in the south of Iran. Also it may point to "اورمزد" or _Ourmozd_ which is middle/ancient Persian name for the planet _Jupiter_ and derived from the term _Ahura Mazda_ or the Avestan term for God. 

## How to run (transformers)

### Install transformers

```
pip install transformers --upgrade
```

_Note:_ For better performance, you may need to install `accelerate` package as well. 

### Inference 

```python
from transformers import AutoTokenizer, AutoModelForCausalLM

model_id = "mann-e/Hormoz-8B"
tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForCausalLM.from_pretrained(model_id).to("cuda")

messages = [{"role": "user", "content": "What is the answer to universe, life and everything?"}]
input_ids = tokenizer.apply_chat_template(messages, tokenize=True, add_generation_prompt=True, return_tensors="pt").to("cuda")

gen_tokens = model.generate(
    input_ids, 
    max_new_tokens=1024, 
    do_sample=True, 
    temperature=1.0,
    )

gen_text = tokenizer.decode(gen_tokens[0])
print(gen_text)
```

## License 

This model is published under _MIT_ license. 

### Commercial Use 

Since this model is MIT licensed, you're free to do whatever you want with the model. However since we're a relatively small startup, we recommend you if you are a big corporate and you host this model, give us a capacity of your API as well. This way, we both can benefit from the model. 