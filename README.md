<div align="center">
🧠 Alpie Core: 4-bit Quantized Reasoning Model

🏆 First 4-bit Reasoning Model from India | Top Performance on Global Leaderboards

🚀 [Quick Start](#rocket-quick-start) • 📊 [Benchmarks](#bar_chart-benchmark-results) • 💡 [Examples](#bulb-usage-examples) • 📖 [Technical Report](https://github.com/169Pi/Alpie-Core-Project/blob/main/docs/Alpie_Core.pdf) • 🤝 [Contributing](#handshake-contributing)
</div>

## ⭐ Highlights
- ⚡ **Efficient**: 4-bit quantized with 16GB VRAM footprint - runs on commodity GPUs
- 🧮 **Strong STEM**: 92.75% on GSM8K, 81.28% on MMLU, 70% on MATH-500
- 🌍 **Indian Context**: Optimized for competitive exams (JEE, NEET, UPSC) with multilingual support
- 🔓 **Open Source**: Apache 2.0 license for research and commercial use

## 📋 Model Overview

Alpie Core is one of the first fine-tuned 4-bit reasoning models from India, and among one of the first worldwide. Trained on just 8 Hopper GPUs using LoRA for parameter-efficient fine-tuning, combined with QLoRA 4-bit quantization, and synthetic STEM-rich dataset distillation, it proves that aggressive quantization can not only match but also surpass full-precision baselines.

| Specification | Details |
|---------------|---------|
| Parameters | 32 billion (4-bit quantized) |
| Architecture | DeepSeek-R1-Distill-Qwen-32B |
| Context Length | 65K tokens |
| Max Output | 16,384 tokens |
| Training Method | LoRA/QLoRA with synthetic STEM data |
| Quantization | 4-bit NF4 with double quantization |

## 📊 Benchmark Results

### Core Benchmarks

<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/combined_benchmark.png?raw=true" alt="Combined Benchmark Results" width="800"/>
</div>

| **Benchmark** | **Alpie Core (32B-4bit)** | **DeepSeek-V2 (236B)** | **Qwen2.5 72B** | **Llama 3.1 405B** | **Llama 3.1 70B** | **Gemma-3 27B-PT** | **Mistral-Small-24B-Base-2501** |
|---------------|---------------------------|-------------------------|------------------|--------------------|--------------------|---------------------|----------------------------------|
| **MMLU (5-shot)** | **81.28%** | 78.4% | 85.0% | 84.4% | 79.3% | 78.6% | 80.73% |
| **GSM8K (8-shot)** | **92.75%** | 81.6% | 88.3% | 83.5% | - | 82.2% | 80.73% |
| **BBH (3-shot)** | **85.12%** | 78.8% | 79.8% | 82.9% | 81.6% | 77.7% | - |
| **MMLU-Pro (5-shot)** | **64.78%** | 51.4% | 58.3% | 52.8% | 53.8% | 52.2% | 54.37% |
| **MBPP (pass@1)** | **75.20%** | 65.0% | 72.6% | 68.4% | - | 65.6% | 69.64% |
| **HumanEval (pass@1)** | **57.23%** | 43.3% | 53.0% | 54.9% | - | 48.8% | - |

These results demonstrate Alpie Core's ability to rival or surpass leading proprietary and open-source models, despite being 4-bit quantized.

### Individual Benchmark Visualizations

<table>
<tr>
<td width="50%">
<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/GSM8K%20(1).png?raw=true" alt="GSM8K Performance" width="100%"/>
<br><b>GSM8K Performance</b>
</div>
</td>
<td width="50%">
<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/BBH.png?raw=true" alt="BBH Performance" width="100%"/>
<br><b>BBH Performance</b>
</div>
</td>
</tr>
<tr>
<td width="50%">
<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/AIME.png?raw=true" alt="AIME Performance" width="100%"/>
<br><b>AIME Performance</b>
</div>
</td>
<td width="50%">
<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/HLE.png?raw=true" alt="Humanity's Last Exam Performance" width="100%"/>
<br><b>Humanity's Last Exam Performance</b>
</div>
</td>
</tr>
</table>

### Leaderboard Performance

#### 🏆 SWE-Bench Verified Performance

<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/swe.png?raw=true" alt="SWE-Bench Performance" width="600"/>
</div>

| **Rank** | **Model** | **Accuracy (%)** | **Performance vs Alpie** |
|----------|-----------|------------------|---------------------------|
| **1** | **Alpie Core** | **57.8** | **Alpie** |
| 2 | Qwen3-Coder-30B-A3B-Instruct | 51.6 | Below Alpie |
| 3 | o1 | 48.9 | Below Alpie |
| 4 | o3-mini (high) | 49.3 | Below Alpie |
| 5 | Claude 3.5 Sonnet | 49.0 | Below Alpie |
| 6 | DeepSeek R1 | 49.2 | Below Alpie |
| 7 | Devstral | 46.8 | Below Alpie |

#### 🧠 Humanity's Last Exam Leaderboard Performance

| **Rank** | **Model** | **Accuracy (%)** | **Performance vs Alpie** |
|----------|-----------|------------------|---------------------------|
| 1 | GPT 4.5 Preview | 5.8 | Above Alpie |
| 2 | Claude Sonnet 4 | 5.42 | Above Alpie |
| **3** | **Alpie Core 32B (4-bit)** | **5.41** | **Alpie** |
| 4 | Llama 4 Maverik | 5.34 | Below Alpie |
| 5 | GPT 4.1 | 4.97 | Below Alpie |
| 6 | Kimi K2 Instruct | 4.68 | Below Alpie |
| 7 | DeepSeek V3 | 4.55 | Below Alpie |
| 8 | Gemini 1.5 Pro 002 | 4.55 | Below Alpie |

### Additional Benchmarks

| **Benchmark** | **Alpie Core (32B-4bit)** | **Category** |
|---------------|---------------------------|--------------|
| **AIME** | **47.34%** | Advanced Mathematics |
| **GPQA (Diamond)** | **40.91%** | Graduate-level QA |
| **TruthfulQA (MC2)** | **60.05%** | Truthfulness |
| **HellaSwag** | **84.66%** | Commonsense |
| **PIQA** | **83.24%** | Physical Reasoning |
| **ARC Challenge** | **67.58%** | Science QA |
| **CommonSenseQA** | **87.06%** | Commonsense |
| **AGIEval** | **64.98%** | General Intelligence |
| **Winogrande** | **79.53%** | Commonsense Reasoning |
| **MATH-500** | **70.00%** | Advanced Mathematics |

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

## 🔧 Advanced Usage

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

## ⭐ Use Cases

- 🎓 **Education**: STEM tutoring, competitive exam preparation
- 💻 **Coding**: Algorithm implementation, code review, debugging
- 🔬 **Research**: Mathematical proofs, scientific analysis
- 📝 **Content**: Technical writing, documentation
- 🌍 **Multilingual**: Hindi/Hinglish support for Indian users

## 📈 Performance Metrics

### System Requirements

| **Deployment** | **Memory** | **GPU** | **Performance** |
|----------------|------------|---------|-----------------|
| Basic | 16GB VRAM | RTX 4090 | ~20 tokens/sec |
| Optimized | 32GB VRAM | A100 | ~50 tokens/sec |
| Production | 80GB VRAM | H100 | ~100 tokens/sec |

### Environmental Impact

<div align="center">
<img src="https://github.com/169Pi/Alpie-Core-Project/blob/main/figures/carbon_footprint.png?raw=true" alt="Carbon Footprint Analysis" width="600"/>
</div>

- **Training Carbon Footprint**: ~298-835 kg CO₂e
- **2-3x more efficient** than FP16 training
- **Sustainable AI**: Optimized for deployment efficiency

## 🔬 Technical Details

- **Quantization**: 4-bit NF4 with double quantization
- **Fine-tuning**: LoRA (rank=16, alpha=16, dropout=0.05)
- **Training Hardware**: 8× NVIDIA H100-80GB
- **Base Model**: DeepSeek-R1-Distill-Qwen-32B

For comprehensive technical information, please refer to our [Technical Report](https://github.com/169Pi/Alpie-Core-Project/blob/main/docs/Alpie_Core.pdf).

## 📚 Datasets

Our training leverages four specialized datasets:

- **ExamBench**: Competitive exam questions
- **Indic Reasoning**: Indian context reasoning
- **Medical Psychology**: Healthcare domain
- **Indian Law**: Legal reasoning

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

- 🐛 [Report bugs](https://github.com/169Pi/Alpie-Core-Project/issues) via Issues
- 💡 [Suggest features](https://github.com/169Pi/Alpie-Core-Project/discussions) via Discussions
- 🔄 [Submit improvements](https://github.com/169Pi/Alpie-Core-Project/pulls) via Pull Requests

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

- [DeepSeek AI](https://deepseek.com) for the foundational model
- [Hugging Face](https://huggingface.co) ecosystem (Transformers, PEFT)
- Open-source community datasets and benchmarks
- Global AI research community for continued inspiration

## 📞 Contact

- **Technical Support**: contact@169pi.com
- **GitHub**: [@169Pi](https://github.com/169Pi)
- **Hugging Face**: [169Pi](https://huggingface.co/169Pi)

---

<div align="center">

🚀 **Empowering the future of AI from India to the world**

Made with ❤️ by 169Pi AI

</div>
