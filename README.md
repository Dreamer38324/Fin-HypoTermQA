# Fin-HypoTermQA: Financial Terminology QA Generation & Evaluation System

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue" alt="Python Version">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License">
  <img src="https://img.shields.io/badge/Status-Active-brightgreen" alt="Project Status">
</p>

## 📋 Overview

Fin-HypoTermQA is a comprehensive financial terminology question-answering generation and automated evaluation system designed to provide high-quality QA datasets for financial education and knowledge testing. The system encompasses complete workflows including data preprocessing, multi-model QA generation, result merging, and LLM-based automatic evaluation.

## 🗂️ Project Structure

```
Fin-HypoTermQA 2/
├── Code/                          # Main project code directory
│   ├── data/                      # Dataset directory
│   │   ├── 3000data/             # 3000 QA pairs
│   │   ├── 500data/              # 500 QA pairs
│   │   ├── 50data/               # 50 test pairs
│   │   └── extract_questions_by_terms.py  # Term-based question extraction script
│   ├── deepseek/                  # DeepSeek model related code
│   │   ├── dataSet/              # DeepSeek output datasets
│   │   ├── main.py               # DeepSeek main program
│   │   ├── unified_generator.py  # DeepSeek unified generator
│   │   ├── prompts.py            # DeepSeek prompt templates
│   │   ├── remove_second_term.py # Second term removal processing
│   │   └── input.csv             # Input data file
│   ├── qwen/                      # Qwen model related code
│   │   ├── dataSet/              # Qwen output datasets
│   │   ├── main.py               # Qwen main program
│   │   ├── unified_generator.py  # Qwen unified generator
│   │   ├── prompts.py            # Qwen prompt templates
│   │   ├── remove_second_term.py # Second term removal processing
│   │   └── input.csv             # Input data file
│   ├── llmJudge/                  # LLM evaluation system
│   │   ├── answer/               # Evaluation results
│   │   ├── PJ/                   # Evaluation project data
│   │   ├── main.py               # Evaluation main program
│   │   ├── evaluator.py          # Core evaluator
│   │   ├── judge.PY              # Judge module
│   │   └── llmproject.py         # LLM project management
│   ├── table/                     # Table data
│   │   ├── FinRAD_Full_13000.csv # Complete FinRAD dataset
│   │   └── step1_breeding_pairs_mpnet.csv  # Pairing data
│   ├── FinRAD_Financial_Readability_Assessment_Dataset-main/  # FinRAD readability assessment dataset
│   ├── old/                       # Legacy code backup
│   ├── .env                       # Environment variables configuration
│   ├── generator.py               # Universal generator
│   ├── dataHandle.py              # Data processor
│   ├── validator.py               # Data validator
│   ├── merge_jsonl_by_question.py # JSONL file merging by question
│   ├── merge_jsonl_by_question_v2.py # Enhanced merging tool V2
│   ├── FinancialDataPreprocessor.py # Financial data preprocessor
│   └── Fin-HypoTermQAone.ipynb    # Main Jupyter notebook
```

## 🔧 Core Functional Modules

### 1. Data Preprocessing Module
- **FinancialDataPreprocessor.py**: Financial data preprocessor for raw data cleaning and formatting
- **dataHandle.py**: Data processor providing data loading, transformation, and saving functions
- **extract_questions_by_terms.py**: Term-dimension question extraction and organization

### 2. Multi-Model QA Generation
#### DeepSeek Model (deepseek/)
- Supports multiple prompt templates (Standard, Linguistic, Background, Scenario)
- Unified generator interface
- Automatic term processing and removal functionality

#### Qwen Model (qwen/)
- Similar functionality implementation to DeepSeek
- Independent prompt strategies
- Parallel processing capabilities

### 3. Result Merging & Processing
- **merge_jsonl_by_question.py**: Merge outputs from different models by question type
- **merge_jsonl_by_question_v2.py**: Enhanced merging tool V2
- Supports multiple data format conversions

### 4. LLM Automated Evaluation System (llmJudge/)
- Automated QA quality evaluation
- Multi-dimensional scoring mechanism
- Batch processing and report generation capabilities

## ⚙️ Environment Configuration

### Required Environment Variables
Configure corresponding API keys in `.env` files in each subdirectory:
```bash
DEEPSEEK_API_KEY=your_deepseek_api_key_here
QWEN_API_KEY=your_qwen_api_key_here
LLM_JUDGE_API_KEY=your_judge_api_key_here
```

### Dependencies Installation
```bash
pip install pandas numpy jsonlines openai python-dotenv
```

## 🚀 Quick Start Guide

### 1. Data Preparation
```bash
# Preprocess raw financial data
python FinancialDataPreprocessor.py

# Extract questions by terms
python data/extract_questions_by_terms.py
```

### 2. QA Generation
```bash
# Run DeepSeek model generation
cd deepseek
python main.py

# Run Qwen model generation  
cd ../qwen
python main.py
```

### 3. Result Merging
```bash
# Merge results from different models
python merge_jsonl_by_question.py
python merge_jsonl_by_question_v2.py
```

### 4. Automated Evaluation
```bash
# Run LLM evaluation
cd llmJudge
python main.py
```

## 📊 Dataset Specifications

### Input Data Formats
- **CSV Format**: Contains basic information like terms and definitions
- **JSONL Format**: Used for storing QA pair data

### Output Data Structure
```json
{
  "term": "financial_term",
  "question": "generated_question",
  "answer": "standard_answer",
  "difficulty": "difficulty_level",
  "category": "question_type"
}
```

### Data Scale
- **50 entries**: Small-scale test data
- **500 entries**: Medium-scale validation data
- **3000 entries**: Large-scale production data

## 🤖 Model Comparison

| Feature | DeepSeek | Qwen |
|---------|----------|------|
| Prompt Strategies | 4 templates | 4 templates |
| Processing Speed | Fast | Medium |
| Output Quality | High | Very High |
| Cost Efficiency | Good | Optimal |

## 📈 Evaluation Metrics

The LLM evaluation system includes the following dimensions:
- **Accuracy**: Answer correctness evaluation
- **Completeness**: Answer content completeness
- **Clarity**: Expression clarity
- **Relevance**: Relevance to the question

## ⚠️ Important Notes

1. **API Key Security**: Safeguard API keys from all platforms
2. **Data Privacy**: Comply with regulations when handling financial data
3. **Cost Control**: Monitor API call costs during large-scale generation
4. **Environment Compatibility**: Pay attention to path separators when running on Windows

## 🛠️ Troubleshooting

Common issues and solutions:
1. **API Call Failures**: Check network connectivity and API key validity
2. **Data Format Errors**: Confirm input file formats meet requirements
3. **Memory Insufficient**: Reduce batch processing size or increase system memory
4. **Encoding Issues**: Ensure files use UTF-8 encoding

## 👥 Development Team

This project is developed by a financial AI research team, focusing on intelligent QA system construction in the financial education domain.

## 📄 License

This project is for academic research and educational purposes only.

---
<p align="center">
  <em>Last Updated: February 2026</em>
</p>
