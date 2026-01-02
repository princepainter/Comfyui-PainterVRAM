# Comfyui-PainterVRAM  
**English** | [中文](#中文)
<img width="1451" height="415" alt="image" src="https://github.com/user-attachments/assets/4feefb06-a100-485c-9811-7f09bcae6085" />

## English  
A tiny ComfyUI custom node that reserves GPU VRAM before workflow execution to avoid OOM crashes.  
Pick **Manual** to set the exact GB, or **Auto** to let the node calculate it from current usage; enable **Clean GPU before** for an instant memory purge.  
No seeds, no extra outputs—just plug and go.

### Install  
1. Clone or download this repo into `ComfyUI/custom_nodes/`  
   ```bash
   git clone https://github.com/princepainter/Comfyui-PainterVRAM.git
   ```
2. Restart ComfyUI → find **Painter VRAM ⚙️** in the **VRAM** category.

### Inputs  
| Name               | Type    | Description |
|--------------------|---------|-------------|
| reserved           | FLOAT   | GB to reserve (used in Manual mode or as offset in Auto) |
| mode               | COMBO   | `manual` = fixed GB, `auto` = current-used + reserved |
| clean_gpu_before   | BOOLEAN | Run garbage-collect + unload models before applying |
| anything           | ANY     | Optional passthrough (returns ExecutionBlocker if None) |

### Output  
| Name   | Type | Description |
|--------|------|-------------|
| output | ANY  | Passthrough value (won’t block execution) |

---

## 中文  
一个简单的 ComfyUI 自定义节点，在工作流运行前预留显存，防止爆显存。  
**手动**模式直接设定 GB 数，**自动**模式按当前已用显存+偏移量计算；勾选 **Clean GPU before** 可立即清理显存。  
无种子、无额外输出口，即插即用。

### 安装  
1. 克隆或下载本仓库到 `ComfyUI/custom_nodes/`  
   ```bash
   git clone https://github.com/princepainter/Comfyui-PainterVRAM.git
   ```
2. 重启 ComfyUI → **VRAM** 类别中找到 **Painter VRAM ⚙️**。

### 输入参数  
| 名称               | 类型    | 说明 |
|--------------------|---------|------|
| reserved           | FLOAT   | 预留显存（GB）；手动模式下为固定值，自动模式下为偏移量 |
| mode               | 下拉框  | `manual` 固定预留，`auto` 按当前已用+偏移计算 |
| clean_gpu_before   | 布尔    | 应用前强制清理显存（垃圾回收+卸载模型） |
| anything           | 任意    | 可选透传输入（不连时返回 ExecutionBlocker） |

### 输出  
| 名称   | 类型 | 说明 |
|--------|------|------|
| output | 任意 | 透传输入值，不阻塞后续节点 |
