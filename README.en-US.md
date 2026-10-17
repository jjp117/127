# JJP Privacy Lens

> Offline EXIF/IPTC/XMP metadata analysis and sanitization engine

[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Privacy](https://img.shields.io/badge/Privacy-Local%20Only-brightgreen)](#)
[![Network](https://img.shields.io/badge/Network-Zero%20Requests-red)](https://jjpgps.pages.dev)

👉 **[Live Demo](https://jjpgps.pages.dev)** | [中文版](./README.md)

## ⚡ Capabilities

| Module | Function | Implementation |
|--------|----------|----------------|
| **Metadata Parsing** | Extracts GPS, timestamps, device serials, software signatures from all IFDs | `exifr` v7.x (client-side parser) |
| **Offline Geocoding** | Lat/Lon → Chinese city names (province/city precision) | BBox collision detection + static dataset |
| **Full Sanitization** | Removes all non-render-critical fields; preserves Width/Height/BitDepth/ColorType | Canvas blob reconstruction |
| **Security Model** | Zero egress, zero persistence, zero telemetry | Browser-sandboxed execution |

## 🛠️ Usage

1. Visit [jjpgps.pages.dev](https://jjpgps.pages.dev) or download ZIP and open `index.html`
2. Drag in a JPG/PNG/HEIC image
3. Review metadata panel (sensitive items highlighted red)
4. Click bottom **"Purge Metadata"** button
5. Browser auto-downloads clean `.png` (original filename preserved)

## ⚠️ Known Limitations

- **Format Coverage**: JPEG/PNG/HEIC only; no RAW/TIFF/DNG support
- **Precision Boundary**: BBox matching is rectangular approximation, not polygonal geofencing; remote areas may fall back to raw coordinates
- **Irreversibility**: EXIF stripping cannot be undone; backup before use
- **Language Status**: Current UI defaults to Chinese; EN/ZH toggle scheduled for v1.1

## License
MIT © [jjp-labs](https://github.com/jjp117)