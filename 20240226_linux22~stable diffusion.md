**2024.02.26**

## stable diffusion本地
https://huggingface.co/stabilityai/sdxl-turbo

### python创建虚拟机
```
python3 -m venv .env
source .env/bin/activate
```

### pip安装包
```
pip3 install diffusers transformers accelerate --upgrade
```
### huggingface下载模型失败，更换源
```
export HF_ENDPOINT="https://hf-mirror.com"
```
### macos下没有cuda，改成mps
```
import diffusers
from diffusers import AutoPipelineForText2Image
import torch
import os 
os.environ['HF_ENDPOINT'] = 'https://hf-mirror.com'



pipe = AutoPipelineForText2Image.from_pretrained("stabilityai/sdxl-turbo", torch_dtype=torch.float16, variant="fp16")
pipe.to("mps")

#prompt = "A cinematic shot of a baby racoon wearing an intricate italian priest robe."
prompt = "A train is running on the railway, while the railway has been destroyed by flood."

image = pipe(prompt=prompt, num_inference_steps=1, guidance_scale=0.0).images[0]
image.show()
```