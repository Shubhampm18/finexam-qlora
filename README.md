# FinExam: QLoRA Fine-Tuning

## Overview

FinExam is a fine-tuning project focused on adapting a language model for financial exam preparation, particularly topics relevant to RBI and SEBI examinations.

The project uses Quantized Low-Rank Adaptation (QLoRA) to fine-tune an instruction-tuned model on financial multiple-choice questions.

## Model

- **Base model:** [Qwen2.5-1.5B-Instruct](https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct)
- **Fine-tuning method:** QLoRA
- **Environment:** Google Colab
- **GPU:** NVIDIA Tesla T4

## QLoRA Configuration

- **Quantization:** 4-bit
- **Quantization type:** NF4
- **Double quantization:** Enabled
- **Compute data type:** FP16
- **LoRA approach:** Parameter-efficient fine-tuning
- **Training objective:** Causal language modeling

## Repository Structure

```text
finexam-qlora/
├── README.md
├── requirements.txt
└── notebooks/
    └── finexam_qlora_training.ipynb
```

## Requirements

- Python and PyTorch
- Transformers
- PEFT
- TRL
- BitsAndBytes
- Accelerate
- Datasets

Install dependencies using:

```bash
pip install -r requirements.txt
```

## Getting Started

1. Clone or download this repository.
2. Open the training notebook in Google Colab.
3. Select a GPU runtime.
4. Install the required dependencies.
5. Configure access to the private dataset and saved model adapter.
6. Run the notebook cells to prepare the data, fine-tune the model, and save the adapter.

## Dataset and Privacy

The project uses a privately maintained financial multiple-choice question dataset. The dataset and its splits are not publicly distributed through this repository.

Access to the dataset and trained adapter is managed separately.

## Limitations

This project is intended for educational and experimental use. Model responses may contain incorrect, incomplete, or outdated financial information. Verify important answers against reliable, current sources.


