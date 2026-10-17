<h4 align="left">
  <span style="margin:0 10px;color:#24292f">English</span>
  <a href="./README.md">简体中文</a>
</h4>
<p align="center">
<img src="https://jjpgps.pages.dev/preview.png" width="300"/>
</p>
<h1 align="center">JJP｜Local EXIF Metadata Analysis & Sanitization Engine</h1>
<p align="center">
Static web implementation. All computations execute within the browser's local sandbox. User images are never uploaded to any remote server.
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
<img src="https://img.shields.io/badge/🔗Access Now‑Privacy Lens-2563eb?style=for-the-badge&logo=https://jjpgps.pages.dev/&logoColor=white" width="320" alt="Open Privacy Lens">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/127/releases" target="_blank">
<img src="https://img.shields.io/badge/📥Download Source-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="Download Source">
</a>
</p>

# JJP Privacy Lens
## What is this
JJP Privacy Lens is a pure client-side image processing tool designed for deep inspection and thorough sanitization of EXIF/IPTC/XMP metadata in digital images. It converts hidden GPS coordinates, device fingerprints, and timestamps into human-readable text and provides a one-click full-stripping solution.

## Design Goal
The goal is to provide privacy-conscious users with a zero-trust, zero-dependency data desensitization method. Users need no software installation, no environment configuration, and no internet connection (after initial load) to complete the process from "risk discovery" to "risk elimination."

## Execution Mode
Runs entirely locally in the browser. All parsing and reconstruction operations are based on HTML5 Canvas API and JavaScript logic, independent of any backend services, generating no network requests beyond the initial page load.

## Core Feature: Offline Geocoding
Includes a lightweight Bounding Box (BBox) database (`china_cities_bbox.txt`) containing latitude/longitude boundaries for major Chinese cities and global hubs. When GPS info is detected, the algorithm matches the nearest city name (e.g., "Beijing", "Shanghai") via rectangle collision detection in real-time, without calling external APIs like Baidu/Amap/Google Maps. If no match is found, raw coordinates are displayed for manual lookup.

## Sanitization Mechanism: Whitelist Filtering
Executes a strict whitelist strategy. Retains only header fields necessary for rendering (Width, Height, BitDepth, ColorType), removing all other tags (including GPSInfo, DateTimeOriginal, Make, Model, Software, Artist, Thumbnail, etc.). Output files are lossless PNG format, ensuring pixel integrity with zero historical traces.

## Usage
Open the web version to start. Drag an image into the page; the right panel automatically lists all metadata items (high-risk items highlighted in red). Confirm and click the bottom button; the browser generates and downloads a sanitized new image. No registration or authorization required.
> Web Version: https://jjpgps.pages.dev/

## ⚠️ Browser Compatibility Notice
Depends on modern browser File API and Canvas API. Latest versions of Chrome, Firefox, Edge, and Safari are recommended. IE series and some older mobile browsers may fail to parse HEIC or ultra-high-resolution images properly.

## Security Statement
This tool provides no cloud storage or logging of any kind. Closing the tab immediately garbage-collects image data from memory. Source code is open-source and auditable; users can self-host for absolute security. However, it cannot prevent physical keylogging or malicious extensions stealing screen content.

## Known Limitations
- **Format Support**: JPG/PNG/HEIC only. Does not support RAW (CR2/NEF/ARW) professional photography formats.
- **Precision Boundary**: BBox matching is rectangular approximation; potential misidentification at administrative borders (not polygonal geofencing).
- **Operation Granularity**: Full-strip mode only; selective retention of specific fields (e.g., keep time but remove GPS) is not supported.
- **Batch Processing**: Current version limited to single-image processing per session.

## License
This project is licensed under the MIT License.