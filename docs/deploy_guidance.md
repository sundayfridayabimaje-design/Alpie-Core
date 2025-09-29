
# Deployment with vLLM

## Option 1: Direct Command Line Deployment

### Install vLLM

```bash
# Install vLLM 0.9.2
pip install vllm==0.9.2

```

### Download Model

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

# Replace with the model you want
model_name = "YOUR_MODEL_NAME"

# Download model and tokenizer
model = AutoModelForCausalLM.from_pretrained(model_name, device_map="auto")
tokenizer = AutoTokenizer.from_pretrained(model_name)

model.save_pretrained("MODEL_PATH")
tokenizer.save_pretrained("MODEL_PATH")
```

Run vLLM directly from the command line:

```bash
CUDA_VISIBLE_DEVICES=0,1 \
HF_HOME=/home/azureuser/.cache/huggingface \
/home/azureuser/vllm_env/bin/vllm serve \
  YOUR_BASE_MODEL \
  --enable-lora \
  --lora-modules reasoning=YOUR_FINE_TUNED_MODEL \
  --dtype auto \
  --tensor-parallel-size 2 \
  --max-model-len 65000 \
  --host 0.0.0.0 \
  --port 8001
```


## Option 2: Create systemd Service File

Create a systemd service file to run vLLM as a background service:

```bash
sudo nano /etc/systemd/system/vllm.service
```

### Service Configuration

Add the following configuration to the service file:

```ini
[Unit]
Description=vLLM Service for Alpie-Core
After=network.target

[Service]
User=azureuser
Group=azureuser
Environment=CUDA_VISIBLE_DEVICES=0,1
Environment=HF_HOME=/home/azureuser/.cache/huggingface
WorkingDirectory=/home/azureuser

ExecStart=/home/azureuser/vllm_env/bin/vllm serve \
  YOUR_BASE_MODEL \
  --enable-lora \
  --lora-modules reasoning=YOUR_FINE_TUNED_MODEL \
  --dtype auto \
  --tensor-parallel-size 2 \
  --max-model-len 65000 \
  --host 0.0.0.0 \
  --port 8001

Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

## Parameter Explanations

### `--enable-lora`
Enables LoRA fine-tuning. LoRA allows you to apply lightweight fine-tuned modules on top of a base model.

### `--lora-modules reasoning=YOUR_FINE_TUNED_MODEL`
Specifies which LoRA modules to apply. In this example, the `reasoning` module is mapped to your fine-tuned model. `YOUR_FINE_TUNED_MODEL` should be replaced with the path or Hugging Face ID of the LoRA-tuned model.

### `--dtype auto`
Sets the data type for the model automatically (float16, bfloat16, etc.) based on GPU capabilities.

### `--tensor-parallel-size 2`
Number of GPUs used for tensor parallelism. Since you set `CUDA_VISIBLE_DEVICES=0,1`, 2 GPUs are used in parallel to handle larger models.

### `--max-model-len 65000`
Maximum sequence length the model can handle. Larger values allow longer input texts, but consume more GPU memory.

## Start the Service

```bash
# Reload systemd daemon
sudo systemctl daemon-reload

# Enable service to start on boot
sudo systemctl enable vllm.service

# Start the service
sudo systemctl start vllm.service

# Check service status
sudo systemctl status vllm.service
```
