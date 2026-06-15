# ESC/FC Current Scale Database & Calculator
# ESC/FC 电流参数数据库与计算器

Extracts factory-calibrated `MILLIVOLT_PER_AMP` values from [AM32](https://github.com/am32-firmware/AM32) ESC firmware source code (`targets.h`) and converts them to flight controller onboard ADC current meter parameters (`ibata_scale`, `ibata_offset`).

从 [AM32](https://github.com/am32-firmware/AM32) 电调固件源码 (`targets.h`) 提取出厂校准值，一键换算飞控板载 ADC 电流计参数（`ibata_scale` / `ibata_offset`）。

---

## Usage 使用

**Online 在线版:** [Open GitHub Pages](https://YOUR_USERNAME.github.io/esc-fc-scale-db/) *(replace with your URL after deploying)*

**Or 本地使用:** Open `index.html` in any browser, click "从 GitHub 拉取" or drag your local `targets.h` file onto the page.

浏览器打开 `index.html`，点击「从 GitHub 拉取」，或拖拽本地的 `targets.h` 到页面上。

## Features 功能

- Parses 260+ ESC targets from AM32 firmware
- Filters by vendor / MCU / keyword
- Calculates `ibata_scale` and `ibata_offset` for Betaflight ADC current meter
- Highlights targets with explicit `MILLIVOLT_PER_AMP` and non-zero `CURRENT_OFFSET`
- Works offline with local file drag & drop

- 解析 AM32 固件 260+ 电调型号
- 按厂商 / 单片机 / 关键词筛选
- 自动计算 Betaflight 板载 ADC 模式的 `ibata_scale` / `ibata_offset`
- 标注显式定义了 MILLIVOLT_PER_AMP 和 CURRENT_OFFSET 的型号
- 支持离线拖拽本地文件

## How it works 原理

```
AM32:  actual_current = (ADC_raw × 3300 / 41 - CURRENT_OFFSET × 100) / MILLIVOLT_PER_AMP
BF:    centiAmps       = (mV × 10000 / ibata_scale + ibata_offset) / 10

ibata_scale  = MILLIVOLT_PER_AMP × 10
ibata_offset = -(CURRENT_OFFSET × 1000) / MILLIVOLT_PER_AMP
```

## Acknowledgments 致谢 & Limitations 局限

本人仅使用过 Betaflight 和 AM32，对其他飞控（iNav / ArduPilot / KISS）和电调固件（BLHeli_S / Bluejay / BLHeli_32）的电流参数映射不熟悉。欢迎这些领域的大佬提 PR 或私信讨论，一起完善这个数据库。

I have only used Betaflight and AM32 personally. I'm not familiar with current parameter mapping for other flight controllers (iNav / ArduPilot / KISS) or ESC firmwares (BLHeli_S / Bluejay / BLHeli_32). PRs and discussions are warmly welcome — let's build this database together.

## License 许可证

MIT
