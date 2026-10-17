# JJP Privacy Lens (隐私透镜)

> 本地化 EXIF 元数据透视与清洗引擎  
> *Offline Metadata Analysis & Sanitization Engine*

[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Privacy](https://img.shields.io/badge/Privacy-Local%20Only-brightgreen)](#)
[![Network](https://img.shields.io/badge/Network-Zero%20Requests-red)](https://jjpgps.pages.dev)

👉 **[在线体验 Live Demo](https://jjpgps.pages.dev)** | [English Version](./README.en-US.md)

## ⚡ 核心能力

| 模块 | 功能描述 | 技术实现 |
|------|----------|----------|
| **深度解析** | 提取 GPS、时间戳、设备序列号、软件签名等所有 IFD 标签 | `exifr` v7.x (Client-side Parser) |
| **离线反查** | 经纬度 → 中文城市名（省级/市级精度），无需联网 | BBox Collision Detection + Static Dataset |
| **全量清洗** | 移除所有非渲染必需字段，仅保留 Width/Height/BitDepth/ColorType | Canvas Blob Reconstruction |
| **安全模型** | 零出站请求、零持久化存储、零遥测上报 | Browser Sandboxed Execution |

## 🛠️ 使用方法

1. 访问 [jjpgps.pages.dev](https://jjpgps.pages.dev) 或下载 ZIP 解压后双击 `index.html`
2. 拖入 JPG/PNG/HEIC 图片
3. 查看右侧元数据面板（敏感项红色高亮）
4. 点击底部 **"Purge Metadata"** 按钮
5. 浏览器自动下载 `.png` 格式净图（原文件名不变）

## ⚠️ 已知局限

- **格式覆盖**：仅支持 JPEG/PNG/HEIC；不支持 RAW/TIFF/DNG
- **精度边界**：BBox 匹配为矩形近似，非多边形精确围栏；偏远地区可能 fallback 至原始坐标
- **不可逆性**：EXIF 剥离后无法恢复，操作前请确认备份
- **语言现状**：当前 UI 默认中文；EN/ZH 切换功能已在 Roadmap 中（v1.1）

## License
MIT © [jjp-labs](https://github.com/jjp117)