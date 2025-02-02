# Hormoz 8B

## Introduction

## Run on [Modal](https://modal.com)

First, you have to go to [modal](https://modal.com) and create an account. Then, you follow their instructions in order to sign your computer to their network and then, you have to follow the following instrcutions.

### Downloading Models

By doing this, you download models in your Modal storage. This means you easily can access model weights and the app doesn't need to download the model from HuggingFace. Remember to set _huggingface secret_ before running the model (although the model is free and not gated, the secret is added in codes. That's just my personal laziness.)

After you set up your account, just run the following code:

```
modal run modal/download_model.py
```

And wait until it downloads the model weights.

### Serving the model 

The only thing you need to do is running the following command:

```
modal serve modal/vllm_inference.py
```

_NOTE:_ Remember to change `my-secret-key` to a more secure API key. Specially if you're gonna use this model on production.

### Deploying the model

## Benchmarks