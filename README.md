<h4 align="right">
  <a href="./README.en-US.md">English</a>
  <span style="margin:0 10px;color:#24292f">简体中文</span>
</h4>
<p align="center">
<img src="https://jjpgps.pages.dev/preview.png" width="300"/>
</p>
<h1 align="center">JJP｜本地化 EXIF 元数据透视与清洗引擎</h1>
<p align="center">
静态网页实现，全部运算在浏览器本地沙箱内执行，用户图片不会上传至任何远端服务器。
</p>
<p align="center">
<a href="https://github.com/jjp117/127/releases">
<img src="https://img.shields.io/github/v/release/jjp117/127?style=flat-square&logo=github" alt="Release">
</a>
<a href="https://github.com/jjp117/127/stargazers">
<img src="https://img.shields.io/github/stars/jjp117/127?style=flat-square&logo=github" alt="Stars">
</a>
<a href="https://github.com/jjp117/127/blob/main/LICENSE">
<img src="https://img.shields.io/github/license/jjp117/127?style=flat-square&logo=github" alt="License">
</a>
</p>
<br>
<p align="center">
<a href="https://jjpgps.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗立即访问‑隐私透镜-2563eb?style=for-the-badge&logo=https://jjpgps.pages.dev/&logoColor=white" width="320" alt="打开隐私透镜">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/127/releases" target="_blank">
<img src="https://img.shields.io/badge/📥下载源码-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="下载源码">
</a>
</p>

# JJP Privacy Lens
## 这是什么
JJP Privacy Lens 是一款纯客户端图像处理工具，用于深度解析并彻底剥离数字图像中的 EXIF/IPTC/XMP 元数据。它能将隐藏的 GPS 坐标、设备指纹、拍摄时间等信息转化为人类可读的文本，并提供一键式的全量清除方案。

## 设计目标
本工具的设计目标是为注重隐私的用户提供一种零信任、零依赖的数据脱敏手段。使用者无需安装软件、无需配置环境、无需联网，仅需通过浏览器即可完成从“发现风险”到“消除风险”的全过程。

## 运行方式
完全运行在浏览器本地。所有解析与重构操作均基于 HTML5 Canvas API 与 JavaScript 逻辑完成，不依赖任何后端服务，不产生任何网络请求（除首次加载页面外）。

## 核心功能：离线地理反查
内置轻量级 Bounding Box (BBox) 数据库 (`china_cities_bbox.txt`)，包含中国主要城市及全球核心城市的经纬度边界框。当检测到 GPS 信息时，算法将通过矩形碰撞检测实时匹配最近的城市名称（如“北京”、“上海”），无需调用百度/高德/Google Maps 等外部 API。若未命中，则显示原始坐标供人工查询。

## 清洗机制：白名单过滤
执行严格的白名单策略。仅保留渲染图像所必需的头部字段（Width, Height, BitDepth, ColorType），移除所有其他标签（包括 GPSInfo, DateTimeOriginal, Make, Model, Software, Artist, Thumbnail 等）。输出文件为无损 PNG 格式，确保像素数据完整且无任何历史痕迹。

## 使用方式
打开网页版即可使用。用户将图片拖入页面，右侧面板自动列出所有元数据项（高危项红色高亮）；确认无误后点击底部按钮，浏览器自动生成并下载净化的新图片。整个过程无需注册、无需授权。
> 网页版：https://jjpgps.pages.dev/

## ⚠️ 浏览器兼容提示
依赖现代浏览器的 File API 与 Canvas API。推荐使用最新版 Chrome, Firefox, Edge, Safari。IE 系列及部分老旧移动端浏览器可能无法正常解析 HEIC 或超大分辨率图片。

## 安全性说明
本工具不提供任何形式的云端存储或日志记录。关闭标签页后，内存中的图像数据即刻被垃圾回收。源代码开源可审计，用户可自行部署以确保绝对安全。但它无法防止物理层面的键盘记录或恶意扩展程序窃取屏幕内容。

## 已知限制
- **格式支持**：仅支持 JPG/PNG/HEIC。不支持 RAW (CR2/NEF/ARW) 等专业摄影格式。
- **精度边界**：BBox 匹配为矩形近似，在城市行政交界处可能存在误判（非多边形围栏）。
- **操作粒度**：提供全量剥离模式，不支持选择性保留特定字段（如只删 GPS 留时间）。
- **批量处理**：当前版本限制为单次处理一张图像。

## 许可
本项目以 MIT 许可证开源。