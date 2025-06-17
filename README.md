# 🧭 Trakr – File Origin Detection Engine

**Trakr** is a lightweight Rust-based engine for determining the **origin** or **provenance** of a file. It identifies where a file came from — such as downloads, email attachments, removable media, or network shares — using metadata analysis and system-level attributes.

Part of the modular analysis suite alongside `Typrr`, `Xtrakt`, `Fyltr`, and others.

---

## 🔍 What It Does

Trakr inspects file system metadata and contextual information to answer:

- Was this file downloaded from a browser?
- Did it arrive via email?
- Was it copied from a USB device?
- Is it from a network share or cloud sync?
- Was it created locally?

It combines OS-level file metadata with heuristic and signature-based detection to classify origin type.

---

## 🚀 Quick Start

### 📦 Requirements

- Rust (1.74+ recommended)
- Linux or Windows (macOS support optional)
- Run with user permissions that allow file metadata access

### 🛠️ Build

```bash
git clone https://github.com/your-org/trakr.git
cd trakr
cargo build --release
````

---

## 🧪 Usage

```bash
trakr --path ./samples/document.pdf
```

### CLI Options

| Flag        | Description                      | Default    |
| ----------- | -------------------------------- | ---------- |
| `--path`    | Path to the file to analyze      | *Required* |
| `--output`  | Output path for JSON result      | `stdout`   |
| `--verbose` | Print internal detection details | `false`    |

---

## 📄 Output

Trakr returns structured JSON with origin classification and supporting signals:

```json
{
  "path": "samples/document.pdf",
  "origin": "downloaded",
  "confidence": 0.92,
  "evidence": {
    "zone_identifier": "ZoneId=3",
    "created_by": "chrome.exe",
    "download_url": "http://example.com/file.pdf"
  }
}
```

Possible origins:

* `downloaded`
* `email_attachment`
* `usb_device`
* `network_share`
* `cloud_synced`
* `local_generated`
* `unknown`

---

## 🧠 Detection Techniques

* **Windows ADS/Zone.Identifier**
* **Extended file attributes (Linux/macOS)**
* **File creation and access metadata**
* **Process lineage (who created the file)**
* **Browser and email client heuristics**
* **USB mount detection**
* **Remote drive/sync folder identification**

---

## 📚 Roadmap

* [x] Windows ADS support
* [x] Basic Linux extended attribute support
* [ ] Cross-platform abstraction layer
* [ ] Confidence scoring calibration
* [ ] Integration with Typrr, Fyltr, Scrbbl

---

## 🛡️ Security Notes

* Trakr does not execute or modify files
* Reads only metadata and system context
* Should be run with appropriate read permissions

---

## 🤝 Contributing

Contributions welcome!

* Open issues for bugs or feature requests
* PRs must pass formatting and test checks

```bash
cargo fmt
cargo clippy
cargo test
```

---

## 📜 License

MIT License © 2025 Your Name or Organization
