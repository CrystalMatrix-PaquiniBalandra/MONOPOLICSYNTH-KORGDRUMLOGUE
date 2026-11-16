# MONOPOLICSYNTH - KORG DRUMLOGUE

**FREE - MONOPOLICSYNTH - KORG DRUMLOGUE**  
**Monopolic - Korg drumlogue**

![Version](https://shields.io)
![Author](https://shields.io)
![Platform](https://shields.io)
![Built with](https://shields.io)

**MONOPOLIC** 是由 **CrystalMatrix (aka Paquini Balandra)** 专为 **Korg drumlogue** 打造的用户合成器，其灵感源自传奇模拟合成器 **Korg Mono/Poly (1981)** 经典的四振荡器架构。

该合成器使用 **Plugdata** 和 **Heavylib** 库进行可视化开发，并通过 **hvcc (Heavy Compiler Collection)** 编译为原生 C++ 代码。它将带有交叉调制（FM）、脉宽调制（PWM）和谐振滤波器的四个 VCO 的丰富音色表现力直接带入 drumlogue 的 **USER** 音轨。

---

## 🎛️ 主要特性

* **四振荡器架构 (`OSC 1` 至 `OSC 4`):**
  * 忠实延续初代 Mono/Poly 的精髓，配备 4 个独立振荡器，支持多种可选波形（*关闭 Off、正弦波 Sine、三角波 Tri、锯齿波 Saw 和脉冲波 Pulse*），并采用 **PolyBLEP** 抗混叠技术。
  * 每个振荡器均支持 **±3 个八度（`-36` 至 `+36` 半音）** 的独立音高调节，同时在 OSC 2、3 和 4 中内置了轻微的模拟失谐（固定 Detune），轻松营造厚重的低音（Bass）、饱满的主音（Lead）以及齐奏（Unison）质感。
* **调制模块 (`FM & PWM`):**
  * 配备专用的调制器振荡器（`FMWAVE`、`FMFREQ`、`FMDEPTH`、`FMGAIN`），可调制出金属质感、打击乐音色及交叉调制效果。
  * 支持实时调节的脉宽调制（`PWM`）。
* **谐振低通滤波器（约 24dB/oct）:**
  * 采用双级 `vcf~` 滤波器串联设计，配备截止频率（`CUTOFF`：20 Hz 至 16 kHz）、谐振（`RES0`）以及专用包络调制（`F.ENV`）。
* **动态包络系统 (`SELADSRS`):**
  * 将 4 个物理控制参数（`ATTACK`、`DECAY`、`SUSTAIN`、`RELEASE`）整合为单一控制模块。通过切换选择器，无需占用过多菜单页面即可分别或同时编辑音量包络（VCA）与滤波器包络（VCF）。
* **智能路由矩阵 (`MACROSEL`):**
  * 通过一个主控制旋钮（`MACRO`）和 22 档选择器（`MACROSEL`）实现集中控制，可精细调节各个振荡器的独立混音电平及调制发送量。

---

## 🎚️ 参数映射表 (`@hv_param`)

Monopolic 在 Korg drumlogue 的 OLED 屏幕上共提供 **23 个参数**：

### 滤波器与宏控制

| # | 屏幕显示名称 | 范围 | 功能说明 |
| :--- | :--- | :--- | :--- |
| **1** | `CUTOFF` | `0.0 - 1.0` | 低通滤波器截止频率（指数曲线）。 |
| **2** | `RES0` | `0.0 - 1.0` | 双级 `vcf~` 滤波器的谐振度。 |
| **3** | `F.ENV` | `0.0 - 1.0` | 包络对滤波器截止频率的调制深度。 |
| **4** | `MACRO` | `0.0 - 1.0` | 调节 `MACROSEL` 所选目标的电平或强度。 |
| **5** | `MACROSEL` | `0 - 21` | 选择 `MACRO` 旋钮所控制的内部参数 *(见下方速查表)*。 |
| **6** | `FMWAVE` | `0 - 5` | 选择 FM 调制器振荡器的波形。 |

### 包络发生器 (ADSR)

| # | 屏幕显示名称 | 范围 | 功能说明 |
| :--- | :--- | :--- | :--- |
| **7** | `SELADSRS` | `0 - 3` | 选择第 8 至 11 号控件所编辑的包络 *(见下方速查表)*。 |
| **8** | `ATTACK` | `0.1 - 1.0` | 起音时间 (Attack)。 |
| **9** | `DECAY` | `0.1 - 1.0` | 衰减时间 (Decay)。 |
| **10** | `SUSTAIN` | `0.1 - 1.0` | 延音电平 (Sustain)。 |
| **11** | `RELEASE` | `0.1 - 1.0` | 释音时间 (Release)。 |

### 振荡器与 FM/PWM 合成

| # | 屏幕显示名称 | 范围 | 功能说明 |
| :--- | :--- | :--- | :--- |
| **12** | `WF1` | `0 - 5` | 振荡器 1 波形 (`0=Off, 1=Sine, 2=Tri, 3=Saw, 4=Pulse`)。 |
| **13** | `WF2` | `0 - 5` | 振荡器 2 波形。 |
| **14** | `WVFORM3` | `0 - 5` | 振荡器 3 波形。 |
| **15** | `WVFORM4` | `0 - 5` | 振荡器 4 波形。 |
| **16** | `OCT1` | `-36 至 +36` | 振荡器 1 音高调谐（半音）。 |
| **17** | `OCT2` | `-36 至 +36` | 振荡器 2 音高调谐 *(内置 +0.15 半音固定失谐)*。 |
| **18** | `OCTAVE3` | `-36 至 +36` | 振荡器 3 音高调谐 *(内置 -0.12 半音固定失谐)*。 |
| **19** | `OCTAVE4` | `-36 至 +36` | 振荡器 4 音高调谐 *(内置 +0.22 半音固定失谐)*。 |
| **20** | `FMFREQ` | `0.0 - 1.0` | FM 调制器振荡器频率。 |
| **21** | `FMDEPTH` | `0.0 - 1.0` | FM 调制深度。 |
| **22** | `FMGAIN` | `0.0 - 1.0` | FM 模块输出增益。 |
| **23** | `PWM` | `0.0 - 1.0` | 脉宽调制 (Pulse Width Modulation)。 |

---

## 🧭 快速参考指南

### 包络选择器 (`7. SELADSRS`)
* **`0`:** 仅编辑 **音量包络 (AMP)**。
* **`1`:** 仅编辑 **滤波器包络 (FILTER)**。
* **`2`:** 同时编辑 **双包络 (AMP + FILTER)**。

### 路由目标矩阵 (`5. MACROSEL`)
使用 `MACROSEL` 参数选择需要通过 `MACRO` 旋钮调节的内部电平：
* **`0`:** 主增益 / 总输出 (`MAIN GAIN`)
* **`1` - `4`:** 各振荡器独立混音电平 (`OSC 1`, `OSC 2`, `OSC 3`, `OSC 4`)
* **`5`:** 干声直通电平 (`DRY LEVEL`)
* **`6` - `13`:** 发送至 PWM 模块的独立电平 (`PWM OSC 1` 至 `OSC 4`)
* **`14` - `20`:** 发送至 FM 模块的独立电平 (`FM OSC 1` 至 `OSC 4`) 及湿声电平 (`WET LEVEL`)

---

## 📥 安装到 Korg drumlogue

1. 从本仓库的 [Releases](../../releases) 页面下载 **`monopolic.drmlgunit`** 文件。
2. 使用 USB 数据线将 Korg drumlogue 连接至电脑。
3. 按住 **[PLAY]** 键的同时开启 drumlogue 电源，进入 **USB Storage Mode（USB 存储模式）**。
4. 将 `monopolic.drmlgunit` 文件复制到以下文件夹中：
   ```text
   /Units/Synths/
   ```
5. 在电脑上安全弹出磁盘，然后重启 drumlogue。
6. 选择 **USER** 音轨，将引擎切换为 **SYNTH** 并找到 **Monopolic**。

## 🛠️ 从源代码编译

如果您希望在 Pure Data 中查看或修改原始补丁（Patch）：

1. 安装 [Plugdata](https://plugdata.org)、[hvcc](https://github.com) 以及 [Korg logue-sdk](https://github.com)。
2. 在 Plugdata 中打开 `.pd` 源文件并针对 `drumlogue` 平台进行编译，或运行以下命令：
   ```bash
   hvcc monopolic.pd -o ./build -n monopolic -g drumlogue
   ```

## 📄 开源协议

本项目基于 **MIT** 协议分发。详情请参阅 [LICENSE](LICENSE) 文件。

---
由 **CrystalMatrix** 用 ❤️ 开发 | 基于 **Plugdata** & **hvcc** 驱动。
