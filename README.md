# test-qwythos

内部镜像：`empero-ai/Qwythos-9B-Claude-Mythos-5-1M`（Qwythos-9B，Apache 2.0）

原始来源：https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M

## 从 Release 下载

模型已打包为分卷 7z 压缩包（单卷约 1.9GB，适配 GitHub Release 2GB 限制）。

### Linux / macOS

```bash
# 安装 7z（如未安装）
# Ubuntu/Debian: sudo apt install p7zip-full
# macOS: brew install p7zip

# 下载所有分卷到同一目录
gh release download v1.0.0 -R zhaoymn/test-qwythos

# 解压
7z x Qwythos-9B-Claude-Mythos-5-1M.7z.001

# 或不用 gh，直接 curl 各分卷 URL
```

解压后得到 `Qwythos-9B-Claude-Mythos-5-1M/` 目录，内含 `model.safetensors`、tokenizer、config 等完整文件。

### Windows

```powershell
gh release download v1.0.0 -R zhaoymn/test-qwythos
& "C:\Program Files\7-Zip\7z.exe" x Qwythos-9B-Claude-Mythos-5-1M.7z.001
```

### 使用 Hugging Face 加载

```python
from transformers import AutoModelForImageTextToText, AutoTokenizer

model_dir = "./Qwythos-9B-Claude-Mythos-5-1M"
tok = AutoTokenizer.from_pretrained(model_dir)
model = AutoModelForImageTextToText.from_pretrained(
    model_dir, dtype="bfloat16", device_map="auto"
)
```

## 校验

Release 附带 `SHA256SUMS.txt`，解压前可校验分卷完整性：

```bash
sha256sum -c SHA256SUMS.txt
```
