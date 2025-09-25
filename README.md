# Alpie-Core-Project
Alpie Core: 4-bit Quantized Reasoning Model - First from India | Top Global Performance
<div align="center">

# 🧠 Alpie Core: 4-bit Quantized Reasoning Model

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Model](https://img.shields.io/badge/🤗%20Hugging%20Face-Model-yellow)](https://huggingface.co/169Pi/Alpie-Core)
[![Datasets](https://img.shields.io/badge/🤗%20Hugging%20Face-Datasets-green)](https://huggingface.co/datasets/169Pi)
[![Paper]([https://img.shields.io/badge/📄-Technical%20Report-red)](./docs/Alpie_Core.pdf](https://huggingface.co/169Pi/Alpie-Core/blob/main/Alpie_Core.pdf))

**🏆 First 4-bit Reasoning Model from India | Top Performance on Global Leaderboards**

[🚀 Quick Start](#quick-start) • [📊 Benchmarks](#benchmark-results) • [💡 Examples](#usage-examples) • [📖 Documentation](./docs) • [🤝 Contributing](./CONTRIBUTING.md)

</div>

---

## 🌟 Highlights

- **🥇 Top Performer**: Ranks #1 on SWE-Bench Verified (57.8%) and #3 on Humanity's Last Exam
- **⚡ Efficient**: 4-bit quantized with 16GB VRAM footprint - runs on commodity GPUs
- **🧮 Strong STEM**: 92.75% on GSM8K, 81.28% on MMLU, 70% on MATH-500
- **🌍 Indian Context**: Optimized for competitive exams (JEE, NEET, UPSC) with multilingual support
- **🔓 Open Source**: Apache 2.0 license for research and commercial use

## 📋 Model Overview

Alpie Core is a 32B parameter language model fine-tuned with 4-bit quantization using LoRA/QLoRA techniques. Built on DeepSeek-R1-Distill-Qwen-32B, it delivers frontier-level reasoning performance while maintaining exceptional efficiency.

| Specification | Details |
|---------------|---------|
| **Parameters** | 32 billion (4-bit quantized) |
| **Architecture** | DeepSeek-R1-Distill-Qwen-32B |
| **Context Length** | 65K tokens |
| **Max Output** | 16,384 tokens |
| **Training Method** | LoRA/QLoRA with synthetic STEM data |
| **Quantization** | 4-bit NF4 with double quantization |

## 📊 Benchmark Results

### Core Benchmarks

| Benchmark | Alpie Core | DeepSeek-V2 | Qwen2.5 72B | Llama 3.1 405B | Llama 3.1 70B |
|-----------|------------|-------------|-------------|----------------|----------------|
| MMLU (5-shot) | **81.28%** | 78.4% | 85.0% | 84.4% | 79.3% |
| GSM8K (8-shot) | **92.75%** | 81.6% | 88.3% | 83.5% | - |
| BBH (3-shot) | **85.12%** | 78.8% | 79.8% | 82.9% | 81.6% |
| HumanEval (pass@1) | **57.23%** | 43.3% | 53.0% | 54.9% | - |
| MBPP (pass@1) | **75.20%** | 65.0% | 72.6% | 68.4% | - |

### Leaderboard Performance

**🏆 SWE-Bench Verified (#1 Global)**
```
1. Alpie Core           57.8%
2. Qwen3-Coder-30B     51.6%
3. o1                  48.9%
4. Claude 3.5 Sonnet   49.0%
5. DeepSeek R1         49.2%
```

**🧠 Humanity's Last Exam (#3 Global)**
```
1. GPT 4.5 Preview     5.8%
2. Claude Sonnet 4     5.42%
3. Alpie Core          5.41%
4. Llama 4 Maverik     5.34%
5. GPT 4.1             4.97%
```

## 🚀 Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/169Pi/Alpie-Core-Project.git
cd Alpie-Core-Project

# Install dependencies
pip install -r requirements.txt

# Alternative: Install with conda
conda env create -f environment.yml
conda activate alpie-core
```

### Basic Usage

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
from peft import PeftModel, PeftConfig
import torch

# Load model and tokenizer
peft_model_id = "169Pi/Alpie-Core"
config = PeftConfig.from_pretrained(peft_model_id)

base_model = AutoModelForCausalLM.from_pretrained(
    config.base_model_name_or_path,
    torch_dtype=torch.float16,
    device_map="auto"
)

tokenizer = AutoTokenizer.from_pretrained(config.base_model_name_or_path)
model = PeftModel.from_pretrained(base_model, peft_model_id)

# Generate response
prompt = "Solve for x: 2x + 5 = 13"
inputs = tokenizer(prompt, return_tensors="pt")

with torch.no_grad():
    outputs = model.generate(**inputs, max_new_tokens=500)
    
response = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(response)
```

## 💡 Usage Examples

<details>
<summary><b>🔬 STEM Problem Solving</b></summary>

```python
# Advanced Mathematics
prompt = """
Solve the integral ∫(x² + 3x - 2)dx from 0 to 4.
Show all steps.
"""

# Physics Problem
prompt = """
A ball is thrown vertically upward with initial velocity 20 m/s.
Calculate the maximum height reached and time taken.
Use g = 9.8 m/s².
"""

# Chemistry Problem
prompt = """
Balance the chemical equation:
C₃H₈ + O₂ → CO₂ + H₂O
Explain the steps involved.
"""
```
</details>

<details>
<summary><b>💻 Coding Challenges</b></summary>

```python
# Algorithm Implementation
prompt = """
Implement a binary search tree in Python with the following methods:
- insert(value)
- search(value)
- delete(value)
- inorder_traversal()

Include proper error handling and documentation.
"""

# System Design
prompt = """
Design a scalable URL shortener like bit.ly.
Include:
- Database schema
- API endpoints
- Caching strategy
- Load balancing approach
"""
```
</details>

<details>
<summary><b>🇮🇳 Indian Context & Competitive Exams</b></summary>

```python
# JEE Mathematics
prompt = """
Find the number of solutions of the equation
sin(x) = x/100 in the interval [0, 2π].
Provide a graphical approach.
"""

# UPSC Current Affairs
prompt = """
Analyze the impact of Digital India initiative on
rural development. Include government schemes
and implementation challenges.
"""

# Hindi/Hinglish Support
prompt = """
Ganit ka sawal: Do trains ek hi direction mein ja rahi hain.
Pehli train 60 km/h, doosri 80 km/h speed mein hai.
Agar distance initially 100 km hai, kitne time baad milegi?
"""
```
</details>

## 🛠️ Advanced Usage

### Streaming Generation

```python
from transformers import TextStreamer

streamer = TextStreamer(tokenizer, skip_prompt=True, skip_special_tokens=True)

outputs = model.generate(
    **inputs,
    max_new_tokens=1000,
    streamer=streamer,
    do_sample=True,
    temperature=0.7,
    top_p=0.9
)
```

### vLLM Deployment

```python
from vllm import LLM, SamplingParams

# Initialize vLLM
llm = LLM(model="169Pi/Alpie-Core", dtype="float16")
sampling_params = SamplingParams(temperature=0.7, top_p=0.95)

# Generate
prompts = ["Explain quantum computing in simple terms."]
outputs = llm.generate(prompts, sampling_params)
```

## 🗂️ Repository Structure

```
📁 Alpie-Core-Project/
├── 📄 README.md                    # This file
├── 📄 LICENSE                      # Apache 2.0 license
├── 📄 requirements.txt             # Python dependencies
├── 📄 environment.yml              # Conda environment
├── 📁 docs/                        # Documentation
│   ├── 📄 Alpie_Core.pdf          # Technical report
│   ├── 📄 INSTALLATION.md         # Detailed installation guide
│   ├── 📄 USAGE.md                # Usage examples
│   └── 📄 API_REFERENCE.md        # API documentation
├── 📁 examples/                    # Example scripts and notebooks
│   ├── 📄 basic_usage.py          # Basic usage example
│   ├── 📄 streaming_demo.py       # Streaming generation
│   ├── 📄 evaluation.py           # Model evaluation
│   └── 📓 interactive_demo.ipynb  # Jupyter notebook
├── 📁 datasets/                    # Dataset documentation
│   ├── 📄 README.md               # Dataset overview
│   ├── 📄 exambench.md            # ExamBench dataset info
│   ├── 📄 indic_reasoning.md      # Indic Reasoning dataset info
│   ├── 📄 medical_psychology.md   # Medical Psychology dataset info
│   └── 📄 indian_law.md           # Indian Law dataset info
├── 📁 scripts/                     # Utility scripts
│   ├── 📄 benchmark.py            # Benchmarking script
│   ├── 📄 deploy_vllm.py          # vLLM deployment
│   └── 📄 convert_model.py        # Model conversion utilities
├── 📁 tests/                       # Unit tests
│   ├── 📄 test_model.py           # Model tests
│   └── 📄 test_utils.py           # Utility tests
└── 📁 .github/                     # GitHub specific files
    ├── 📁 workflows/               # CI/CD workflows
    ├── 📄 ISSUE_TEMPLATE.md       # Issue template
    └── 📄 PULL_REQUEST_TEMPLATE.md # PR template
```

## 🌟 Use Cases

- **🎓 Education**: STEM tutoring, competitive exam preparation
- **💻 Coding**: Algorithm implementation, code review, debugging  
- **🔬 Research**: Mathematical proofs, scientific analysis
- **📝 Content**: Technical writing, documentation
- **🌍 Multilingual**: Hindi/Hinglish support for Indian users

## 📈 Performance Metrics

### System Requirements

| Deployment | Memory | GPU | Performance |
|------------|---------|-----|-------------|
| Basic | 16GB VRAM | RTX 4090 | ~20 tokens/sec |
| Optimized | 32GB VRAM | A100 | ~50 tokens/sec |
| Production | 80GB VRAM | H100 | ~100 tokens/sec |

### Environmental Impact

- **Training Carbon Footprint**: ~298-835 kg CO₂e
- **2-3x more efficient** than FP16 training
- **Sustainable AI**: Optimized for deployment efficiency

## 🔬 Technical Details

- **Quantization**: 4-bit NF4 with double quantization
- **Fine-tuning**: LoRA (rank=16, alpha=16, dropout=0.05)
- **Training Hardware**: 8× NVIDIA H100-80GB
- **Training Duration**: 408 hours
- **Base Model**: DeepSeek-R1-Distill-Qwen-32B

## 📚 Datasets

Our training leverages four specialized datasets:

- **[ExamBench](https://huggingface.co/datasets/169Pi/exambench)**: Competitive exam questions
- **[Indic Reasoning](https://huggingface.co/datasets/169Pi/indic_reasoning)**: Indian context reasoning
- **[Medical Psychology](https://huggingface.co/datasets/169Pi/medical_psychology)**: Healthcare domain
- **[Indian Law](https://huggingface.co/datasets/169Pi/indian_law)**: Legal reasoning

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](./CONTRIBUTING.md) for details.

- 🐛 Report bugs via [Issues](https://github.com/169Pi/Alpie-Core-Project/issues)
- 💡 Suggest features via [Discussions](https://github.com/169Pi/Alpie-Core-Project/discussions)
- 🔄 Submit improvements via [Pull Requests](https://github.com/169Pi/Alpie-Core-Project/pulls)

## 📄 Citation

```bibtex
@misc{169pi2025alpiecore,
  title = {Alpie-Core: A 4-Bit Quantized Reasoning Model from India that Outperforms Full-Precision Models},
  author = {169Pi AI},
  year = {2025},
  url = {https://huggingface.co/169Pi/Alpie-Core},
  note = {Apache 2.0 License}
}
```

## 🙏 Acknowledgments

- **DeepSeek AI** for the foundational model
- **Hugging Face** ecosystem (Transformers, PEFT, vLLM)
- **Open-source community** datasets and benchmarks
- **Global AI research community** for continued inspiration

## 📞 Contact

- **Technical Support**: [contact@169pi.com](mailto:contact@169pi.com)
- **Business Inquiries**: [business@169pi.com](mailto:business@169pi.com)
- **GitHub**: [@169Pi](https://github.com/169Pi)
- **Hugging Face**: [169Pi](https://huggingface.co/169Pi)

---

<div align="center">

**🚀 Empowering the future of AI from India to the world**

Made with ❤️ by [169Pi AI](https://169pi.com)

</div>
