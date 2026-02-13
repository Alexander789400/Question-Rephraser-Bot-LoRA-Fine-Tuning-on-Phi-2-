# Question Rephraser Bot (LoRA Fine-Tuning on Phi-2)

A lightweight **Question Rewriting Assistant** that converts informal or unclear user questions into **clearer, more formal, and grammatically correct** versions using **LoRA fine-tuning** on the **Phi-2 language model**.

---

## Project Overview

Many user questions on the internet are written in an unstructured or informal way:

> "wat is best laptop for ai student?"

This model rewrites them into a more professional form:

> "What is the best laptop for a student studying artificial intelligence?"

This project fine-tunes **Phi-2** using **LoRA (Low-Rank Adaptation)** on the **Quora Question Pairs dataset**.

---

## Objectives

- Load the Quora Question Pairs dataset from HuggingFace  
- Convert question pairs into instruction-response format  
- Apply LoRA configuration to Phi-2  
- Fine-tune the model using `SFTTrainer`  
- Test the model on custom user questions  

---

## Dataset

We use the HuggingFace dataset:

- **AlekseyKorshuk/quora-question-pairs**

Duplicate question pairs are treated as paraphrase examples:

| Input Question | Rewritten Question |
|--------------|-------------------|
| "How to learn coding fast?" | "What is the best way to learn programming quickly?" |

---

##  What is LoRA?

**LoRA (Low-Rank Adaptation)** is a parameter-efficient fine-tuning technique.

Instead of updating all model weights, LoRA:

- Freezes the original model  
- Adds small trainable adapter layers  
- Trains only a tiny fraction of parameters  

This makes fine-tuning faster, cheaper, and memory efficient.

---

## Why LoRA Instead of Full Fine-Tuning?

Full fine-tuning requires updating billions of parameters, which is expensive.

LoRA is preferred because:

- Requires less GPU memory  
- Faster training  
- Prevents overfitting  
- Lightweight adapters are easy to deploy  

---

## Model Used

- **Base Model:** Microsoft Phi-2  
- **Fine-Tuning Method:** LoRA + SFTTrainer  
- **Task:** Question Rewriting / Formal Paraphrasing  

---

## Training Pipeline

1. Load Quora dataset  
2. Filter duplicate pairs  
3. Convert into instruction-response format  
4. Apply LoRA adapters to Phi-2  
5. Train using supervised fine-tuning  
6. Test on custom questions  

---

Observations :

The model successfully rewrites informal queries into formal language

Grammar and clarity improved significantly

Works best on short-to-medium user questions

More training data and epochs can improve paraphrasing quality
