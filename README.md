<p align="center">
  <img width="100%" alt="Synthetic bedside vitals streaming into PRISM, 72 LightGBM sepsis organ-dysfunction models running offline on a microcontroller"  src="https://github.com/user-attachments/assets/7f559ac9-fffc-4b8a-994b-8111e472fbc6" />
</p>


## Harry Nguyen

Biology + CS @ Case Western Reserve University. I work on **efficient deep learning and edge deployment for clinical and biological models**. The goal is to make models small enough to run where the data lives (a bedside monitor, a small lab's benchtop machine, a microcontroller) and to check what they lose when they get there.

Compression usually gets reported as one number: in-distribution accuracy. I care about the rest. Does a compressed model still transfer across hospitals, labs, and devices, and what breaks first when it doesn't?

### Current work

| Project | What it is | Stack |
|---|---|---|
| **PRISM: sepsis at the edge** | Organ-dysfunction prediction in sepsis: 72 LightGBM models (6 organs × 12 horizons) built at the Broad Institute and externally validated across ICU datasets. Now exporting to ONNX so it can run offline on edge hardware, down to microcontrollers, with no cloud dependency at the bedside. | Python, LightGBM, ONNX |
| **Taming the 262K-way output head** | Gemma 3 270M on a Cortex-M55 + Ethos-U85 MCU. The tied embedding / output head is ~168M of the model's ~270M params, so that is where the memory and latency budget goes. Optimizing the vocab projection for on-device decode. | Rust, PyTorch, ExecuTorch |
| **TinyCell** | Compression study for single-cell annotation models: does a model quantized to preserve in-distribution accuracy still hold up on another lab's data? Targets cheap hardware so small labs without a cluster can run it. *Writeup in progress.* | Python, PyTorch |

### Interests

- Offline, on-device clinical risk models
- Post-training quantization (SmoothQuant-style activation smoothing) and quantization + distillation
- Large-vocabulary output heads on memory-constrained hardware
- KV cache compression for long, multimodal inputs
- Robustness of compressed models under site and distribution shift

### Toolbox

**Languages:** Python, Rust, R
**ML:** PyTorch, LightGBM, ONNX, ExecuTorch
**Hardware:** Arm Cortex-M55 + Ethos-U85, NVIDIA DGX Spark (GB10 Grace Blackwell)

<details>
<summary>Gemma 3 270M output-head demo</summary>
<p align="center"><img src="./edge-banner.gif" alt="Quantizing Gemma 3 270M's 262K-way output head from FP32 to INT4 for a Cortex-M55 + Ethos-U85 MCU" width="100%"></p>
</details>

### Elsewhere

Computational biology and genomics packages (VNNBio, oncoPATHr) live at [mxn581-dev](https://github.com/mxn581-dev).
