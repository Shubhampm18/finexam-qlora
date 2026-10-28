# FinExam: QLoRA Fine-Tuning for Financial Exam Preparation

## Overview

FinExam is an experimental fine-tuning project that adapts an instruction-tuned large language model for multiple-choice financial exam preparation, with a focus on Indian financial-sector examinations such as RBI and SEBI exams.

The project uses Quantized Low-Rank Adaptation (QLoRA) to fine-tune `Qwen/Qwen2.5-1.5B-Instruct` on finance-related question-and-answer data.

The objective is to investigate whether parameter-efficient fine-tuning improves the model's ability to answer finance examination questions compared with the original base model.

## Objectives

- Fine-tune an instruction-tuned language model for finance exam-style multiple-choice questions.
- Use QLoRA to reduce the trainable parameter count and training resource requirements.
- Compare the fine-tuned model against the original base model.
- Evaluate overall accuracy and performance across financial topics.
- Document the training configuration, evaluation methodology, results, and limitations.

## Model and Training Setup

| Component | Configuration |
|---|---|
| Base model | `Qwen/Qwen2.5-1.5B-Instruct` |
| Fine-tuning method | QLoRA |
| Training platform | Google Colab |
| GPU | NVIDIA Tesla T4 |
| Reported GPU capacity | Approximately 14.56 GiB |
| Dataset size | 1,000 multiple-choice questions |
| Training split | 800 examples |
| Validation split | 100 examples |
| Test split | 100 examples |
| Training duration | Approximately 29 minutes |
| Training epochs | 3 |
| Training steps | 300 |
| Trainable parameters | 18,464,768 |
| Trainable parameter percentage | Approximately 1.182% |

The detailed quantization, LoRA, and training hyperparameters are documented in the notebook. Exact settings should be taken from the final executed training configuration.

## Dataset

The training dataset contains 1,000 finance-related multiple-choice questions, each with five answer options (A–E).

The dataset was divided into:
- Training: 800 examples
- Validation: 100 examples
- Testing: 100 examples

The dataset is not included in this public repository. It is retained separately in private storage.

## Evaluation Results

The base model and fine-tuned model were evaluated on the same 100-question test set.

| Metric | Base model | Fine-tuned model |
|---|---:|---:|
| Correct answers | 37/100 | 69/100 |
| Accuracy | 37% | 69% |

The fine-tuned model achieved an improvement of 32 percentage points on this test set.

These results describe the evaluated test set and should not be interpreted as a guarantee of performance on all finance examinations.

A separate 30-question comparison produced different results: the base model scored 23/30 and the fine-tuned model scored 20/30 in the initial evaluation. That comparison requires verification of answer parsing and test-question independence before drawing further conclusions.

## Repository Structure

```text
finexam-qlora/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── finexam_qlora_training.ipynb
└── results/
    ├── training_metrics.json
    ├── finetuned_test_summary.json
    ├── finetuned_test_evaluation.csv
    ├── base_test_evaluation.csv
    └── base_vs_finetuned_comparison.csv
```

The `results/` directory is optional. Only publish result files after checking that they do not expose private dataset content or other sensitive information.

## How to Run

1. Open the notebook in Google Colab.
2. Select a compatible GPU runtime.
3. Install the dependencies listed in `requirements.txt`.
4. Authenticate to Google Drive if required.
5. Provide access to the privately stored dataset and saved adapter.
6. Run the notebook cells in order.

Training from scratch requires access to the dataset. Loading the fine-tuned model requires the base model and the saved adapter.

The notebook may need small path adjustments to match your private Google Drive folder structure.

## Model Storage and Privacy

The following assets are intentionally excluded from this public repository:

- The private fine-tuning dataset.
- The saved QLoRA adapter weights.
- Intermediate training checkpoints.
- Private credentials and access tokens.

The adapter and dataset are stored separately in private storage. Access must be granted separately to anyone who needs to reproduce the experiment.

The base model is available from its Hugging Face model repository, subject to its license and usage terms.

## Limitations

- The dataset contains 1,000 examples and has limited topic coverage.
- The main test set contains 100 questions, so the reported accuracy has uncertainty.
- Performance can vary across topics and question difficulty.
- The separate 30-question comparison has not yet been fully verified.
- Correct multiple-choice predictions do not necessarily demonstrate reliable reasoning or factual accuracy.
- The model is an experimental educational tool, not an official RBI or SEBI source or a substitute for checking current regulations.

## Future Work

- Verify the separate evaluation and inspect incorrect predictions.
- Expand and balance the dataset across financial topics.
- Evaluate on a larger independent test set.
- Compare memory use and inference latency under controlled conditions.
- Investigate robustness, factual accuracy, and regulatory knowledge.

## Acknowledgements

This project uses the Qwen2.5 instruction-tuned model and parameter-efficient fine-tuning tools from the Hugging Face ecosystem.

Please refer to the original model documentation and the relevant software licenses before using or redistributing model assets.
