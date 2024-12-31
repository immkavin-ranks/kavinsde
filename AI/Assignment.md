Explain step in creating a AI model with practical example.

I am trying to create a chat bot for my portfolio.
Tried OpenAI and their free tier didn't work for me. So i am planning to work with open source llama3. But it can't run in windows environment. 

I am trying to use it in WSL.
Installing conda in WSL using https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da

conda create -n portfolioAI python=3.12 *anaconda*
the anaconda keyword at the end installed whole bunch of tools, omit that if you need simple environment.

used jupyter using 
jupyter notebook --no-browser

https://www.llama.com/llama-downloads/
pip install llama-stack
llama model list

Using lightweight pre trained model
llama model download --source meta --model-id  Llama3.2-3B

use unique URL ;';

model Installed
To run MD5 checksums, use the following command: llama model verify-download --model-id Llama3.2-3B

Is this possible?

Try using transformers
not able to import pip package in jupyter notebook
https://stackoverflow.com/questions/38368318/installing-a-pip-package-from-within-a-jupyter-notebook-not-working


```python
import torch
from transformers import pipeline

model_id = "meta-llama/Llama-3.2-1B"

pipe = pipeline(
    "text-generation", 
    model=model_id, 
    torch_dtype=torch.bfloat16, 
    device_map="auto"
)

pipe("The key to life is")

```

OSError: You are trying to access a gated repo.
Make sure to have access to it at https://huggingface.co/meta-llama/Llama-3.2-1B.
401 Client Error. (Request ID: Root=1-67739751-02a6c6d35ff62b624a68a037;9096b678-0e7f-480f-a3e4-551e78b2d359)

Cannot access gated repo for url [https://huggingface.co/meta-llama/Llama-3.2-1B/resolve/main/config.json](https://huggingface.co/meta-llama/Llama-3.2-1B/resolve/main/config.json).
Access to model meta-llama/Llama-3.2-1B is restricted. You must have access to it and be authenticated to access it. Please log in.


Using gated model gemma 2 google - because i have access.
Jupyter widget not found
https://discourse.jupyter.org/t/error-displaying-widget-model-not-found-how-to-fix-this/11886/3

`jupyter labextension list`
all must enabled OK status

Gated repos gave up 😓

public available
bert-base-uncased
https://huggingface.co/google-bert/bert-base-uncased



